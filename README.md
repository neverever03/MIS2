# MIS2
RBAC权限管理

1.用户test1可以查看的页面（Sys_menu）
![image](https://github.com/neverever03/MIS2/blob/master/RBAC1.PNG)

2.用户test1对订单(order)页面中的操作权限(sys_button)
![image](https://github.com/neverever03/MIS2/blob/master/RBAC2.PNG)

3.伪代码：
      1,  a.	根据用户名直接从权限表中查找权限为可操作页面对应的权限ID
     &amp  b.  For 每一个权限ID
			            从页面表查找到页面编号为权限ID对应的页面名称	
      2,  c.   根据用户名查对应的角色
          d.   For 每一个角色
                    从权限表中查找权限为可操作页面对应的权限ID
		                      For 每一个权限ID
			                        从页面表查找到页面编号为权限ID对应的页面名称	
	
          e.合并1,2的结果
          
          
          
          
          a.根据第一问所查询的结果，查找页面为“订单” 所对应的页面序号（MenuNo）
          b.从按钮表里查找该页面序号对应的按钮ID及按钮名称
          
