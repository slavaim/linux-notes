```ptrace``` sets ```TIF_SYSCALL_TRACE``` flag for a task to trace syscalls

```
static int ptrace_resume(struct task_struct *child, long request,
			 unsigned long data)
{
	bool need_siglock;

	if (!valid_signal(data))
		return -EIO;

	if (request == PTRACE_SYSCALL)
		set_tsk_thread_flag(child, TIF_SYSCALL_TRACE);
	else
		clear_tsk_thread_flag(child, TIF_SYSCALL_TRACE);
[...]
}
```

```do_syscall_trace``` called on each sysycall checks the flag

```
/*
 * Notification of system call entry/exit
 * - triggered by current->work.syscall_trace
 */
asmlinkage void do_syscall_trace(struct pt_regs *regs, int entryexit)
{
	if (!(current->ptrace & PT_PTRACED))
		return;

	if (!test_thread_flag(TIF_SYSCALL_TRACE))
		return;

	/* The 0x80 provides a way for the tracing parent to distinguish
	   between a syscall stop and SIGTRAP delivery. */
	ptrace_notify(SIGTRAP | ((current->ptrace & PT_TRACESYSGOOD) ?
			0x80 : 0));

	/*
	 * this isn't the same as continuing with a signal, but it will do
	 * for normal use.  strace only continues with a signal if the
	 * stopping signal is not SIGTRAP.  -brl
	 */
	if (current->exit_code) {
		send_sig(current->exit_code, current, 1);
		current->exit_code = 0;
	}
}
```
