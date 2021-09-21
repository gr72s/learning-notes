> 1.Greenlet 是 python 的一个 C 扩展，旨在提供可自行调度的‘微线程’， 即协程  
> 2.在 greenlet 中，target.switch（value）可以切换到指定的协程（target）， 然后 yield value。greenlet 用 switch 来表示协程的切换，从一个协程切换到另一个协程需要显式指定。
