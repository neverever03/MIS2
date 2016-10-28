# MIS2
RBAC权限管理

1.用户test1可以查看的页面（Sys_menu）

SELECT MenuID,MenuName
from cf_privilege,sys_menu ,cf_user
WHERE cf_user.LoginName="test1" and cf_privilege.PrivilegeMaster="CF_User"AND
 cf_user.UserID=cf_privilege.privilegeMasterKey AND cf_privilege.PrivilegeAccess="Sys_Menu" 
and cf_privilege.PrivilegeAccessKey=sys_menu.MenuID and cf_privilege.PrivilegeOperation="Permit"
UNION
SELECT MenuID,MenuName
FROM cf_privilege,sys_menu ,cf_user,cf_userrole,cf_role
WHERE cf_user.LoginName="test1" and cf_user.UserID=cf_userrole.UserID and cf_privilege.PrivilegeMaster="CF_Role" 
and cf_privilege.privilegeMasterKey=cf_role.RoleID AND cf_privilege.PrivilegeAccess="Sys_Menu"
and cf_privilege.PrivilegeAccessKey=sys_menu.MenuID and cf_privilege.PrivilegeOperation="Permit"
![image](https://github.com/neverever03/MIS2/blob/master/RBAC1.PNG)

2.用户test1对订单(order)页面中的操作权限(sys_button)

SELECT BtnID ,BtnName
from cf_privilege,sys_menu ,cf_user,sys_button
WHERE cf_user.LoginName="test1" and cf_privilege.PrivilegeMaster="CF_User" AND cf_user.UserID=cf_privilege.privilegeMasterKey
 AND cf_privilege.PrivilegeAccess="Sys_Button" and cf_privilege.PrivilegeAccessKey=sys_button.BtnID 
and cf_privilege.PrivilegeOperation="Permit" and sys_menu.MenuNo=sys_button.MenuNo AND sys_menu.MenuName="订单" 
UNION
SELECT BtnID ,BtnName
FROM cf_privilege,sys_menu ,cf_user,cf_userrole,cf_role,sys_button
WHERE cf_user.LoginName="test1" and cf_user.UserID=cf_userrole.UserID and cf_privilege.PrivilegeMaster="CF_Role" and
 cf_privilege.privilegeMasterKey=cf_role.RoleID AND cf_privilege.PrivilegeAccess="Sys_Button" and 
cf_privilege.PrivilegeAccessKey=sys_button.BtnID and cf_privilege.PrivilegeOperation="Permit" and sys_menu.MenuNo=sys_button.MenuNo  AND sys_menu.MenuName="订单"
![image](https://github.com/neverever03/MIS2/blob/master/RBAC2.PNG)



![image](https://github.com/neverever03/MIS2/blob/master/RBAC3.PNG)









          
