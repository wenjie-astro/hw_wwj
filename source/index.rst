.. hw_wwj documentation master file, created by
   sphinx-quickstart on Sat Jan 29 21:16:20 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

hw_wwj 程序的介绍文件
==================================
hw_wwj是一个测试文档，

里面有hw1(r1, r2)，hw2(r1, r2)，s=hw3(r1, r2)三个函数，功能就是求sin

测试fortran和python混合编程

fortran的程序和python的程序分别如下：

fortran-hw1
--------------

这是一个函数，用来求出r1和r2的和的sin值

.. code-block:: fortran
	
	real*8 function hw1(r1, r2)
	real*8 :: r1, r2
	!f2py intent(in) r1
	!f2py intent(in) r2
	hw1 = sin(r1 + r2)
	print*, hw1
	return
	end function hw1

fortran-hw2
------------

这是一个函数，用来求出r1和r2的和的sin值

.. code-block:: fortran

	subroutine hw2(r1, r2)
	real*8 :: r1, r2, s
	!f2py intent(in) r1
	!f2py intent(in) r2
	s = sin(r1 + r2)
	print*, 'Hello, World!, sin(',r1+r2,')=',s
	return
	end subroutine hw2
	
fortran-hw3
---------------

这是一个函数，用来求出r3和r4的和的sin值

.. code-block:: fortran

	subroutine hw3(r3, r4, s)
	! integer, intent(in) :: r3, r4 这里不能用integer（整型），否则会报错
	real, intent(in) :: r3,r4
	real, intent(out) :: s
	!f2py intent(in) r3
	!f2py intent(in) r4
	!f2py intent(out) s
	s = sin(r3 + r4)
	return
	end

python-wwjf2p
---------------

这是一个函数包中，不同的程序互相调用的例子，python调用fortran文件，并且还要能够完美的运行。

.. code-block:: python

	import hw_wwj.hw_fortran_t as hw
	#from hw_wwj import hw_fortran_t as hw

	def test():
		a=1.0
		b=2.0
		print('call func hw1')
		hw.hw1(a,b)
		print('******************') 
		print('call func hw2')
		hw.hw2(a,b)
		print('******************') 
		print('call func hw3') 
		c=hw.hw3(a,b)
		print('c',c)

.. toctree::
   :maxdepth: 2
   :caption: User Guide:
   
   install
   use
   



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
