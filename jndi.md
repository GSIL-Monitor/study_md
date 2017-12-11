#### 方式一: 
1. web.xml中加入(此步可以不需要)

   ```xml
   <resource-ref>
   	<description>DB Connection</description>
   	<res-ref-name>xxwsuser</res-ref-name>
   	<res-type>javax.sql.DataSource</res-type>
   	<res-auth>Container</res-auth>
   </resource-ref>
   ```
2. conf/context.xml中加入
   ```xml
   <Resource  
       auth="Container"  
       description="demo"  
       name="xxwsuser"  
     	username="root" 
   	password="db@mysql" 
       type="javax.sql.DataSource"  
       driverClassName="com.mysql.jdbc.Driver"  
       url="jdbc:mysql://192.168.102.81:3306/cloudlink_core_framework?useCursorFetch=true&amp;characterEncoding=UTF-8" />
   ```

>  其中web.xml中的res-ref-name值要和context.xml的name值一致

#### 方式二:

1. conf/server.xml中的<GlobalNamingResources>加入(此步可以不需要)

   ```xml
   <Resource  
   	    auth="Container"  
   	    description="demo"  
   	    name="xxwsuser"  
   	  	username="root" 
   		password="db@mysql" 
   	    type="javax.sql.DataSource"  
   	    driverClassName="com.mysql.jdbc.Driver"  
   	    url="jdbc:mysql://192.168.102.81:3306/cloudlink_core_framework?useCursorFetch=true&amp;characterEncoding=UTF-8" />
   ```

   ​

2. conf/context.xml中加入:

   ```xml
   <ResourceLink global="xxwsuser" name="xxwsuser" type="javax.sql.DataSource"/>
   ```

   ​