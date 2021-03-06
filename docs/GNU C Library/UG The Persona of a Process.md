# [进程的角色](https://www.gnu.org/software/libc/manual/html_node/Process-Persona.html#Process-Persona)

在任何时候，每个进程都有一个有效用户号、有效组号和一组辅助组号。这些号决定了进程的特权。它们统称为进程的角色，因为它们确定了“我是谁”，并以此实现访问控制。

当你登录时，登录 **shell** 启动新进程，以你的用户号、你的默认组号、你的辅助号作为角色。通常情况下，你的所有其他进程继承这些值。

进程还有一个真实用户号，标识是谁创建了进程；一个真实组号，标识真实用户的默认组号。这些值，不会参与访问控制，我们不需要把它们纳入角色考虑。不过，它们也是非常重要的。

真实和有效用户号，能够在进程生命期被修改。

最后，有许多操作只能被一个特殊进程执行，用户号是 `0`。这个进程称为“特权进程”，这个用户称为“超级用户”。通常，其用户名是 `root`，但是，也说不定是其他名字。

