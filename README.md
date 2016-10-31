# MIS2
RBAC权限管理

1.用户test1可以查看的页面（Sys_menu）


SELECT MenuID,MenuName
from cf_privilege
LEFT JOIN sys_menu on cf_privilege.PrivilegeAccessKey=sys_menu.MenuID 
WHERE ((cf_privilege.PrivilegeMaster="CF_User" 
			and  cf_privilege.PrivilegeMasterKey=(select UserID from cf_user where cf_user.LoginName="test1"))
OR  (cf_privilege.PrivilegeMaster="CF_Role"  
			and cf_privilege.PrivilegeMasterKey IN(select RoleID  from cf_userrole,cf_user where cf_userrole.UserID=cf_user.UserID and cf_user.LoginName="test1")))
 and cf_privilege.PrivilegeOperation="Permit" and cf_privilege.PrivilegeAccess="Sys_Menu"
![image](https://github.com/neverever03/MIS2/blob/master/RBAC1.PNG)

2.用户test1对订单(order)页面中的操作权限(sys_button)
SELECT BtnID,BtnName
from cf_privilege
LEFT JOIN sys_button on cf_privilege.PrivilegeAccessKey=sys_button.BtnID
LEFT JOIN sys_menu on sys_button.MenuNo=sys_menu.MenuNo
WHERE ((cf_privilege.PrivilegeMaster="CF_User" 
			and  cf_privilege.PrivilegeMasterKey=(select UserID from cf_user where cf_user.LoginName="test1"))
OR  (cf_privilege.PrivilegeMaster="CF_Role"  
			and cf_privilege.PrivilegeMasterKey IN(select RoleID  from cf_userrole,cf_user where cf_userrole.UserID=cf_user.UserID and cf_user.LoginName="test1")))
and sys_menu.MenuName="订单" and cf_privilege.PrivilegeOperation="Permit" and cf_privilege.PrivilegeAccess="Sys_Button" 
![image](https://github.com/neverever03/MIS2/blob/master/RBAC2.PNG)



![image](https://github.com/neverever03/MIS2/blob/master/RBAC3.PNG)









          
