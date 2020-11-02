# php审计相关

0x01. 代码审计两种基本方法：

    正向追踪数据流：跟踪用户输入参数 -> 来到代码逻辑 -> 最后审计代码逻辑缺陷 -> 尝试构造payload
    逆向溯源数据流：字符串搜索指定操作函数 -> 跟踪函数可控参数 -> 审计代码逻辑缺陷 -> 尝试构造payload
    
0x02. PHP相关配置    

        用户可访问目录open_basedir = D:\WWW
        能够控制PHP脚本只能访问指定的目录,这样能够避免PHP脚本访问不应该访问的文件,一定程度上限制webshell的危害 
         
        内部错误选项display_errors = on
        表明实现PHP脚本的内部错误,网站发布后建议关不PHP的错误回显
        
        禁用函数disable_functions
        禁止一些敏感函数的使用
        
        是否允许包含远程文件allow_url_include = off
        该配置为ON的情况下,可以直接包含远程文件,若包含的变量为可控的情况下,可以直接控制变量来执行PHP代码
        
        是否允许打开远程文件allow_url_open = on
        允许本地PHP文件通过调用url重写来打开或者关闭写权限,默认的封装协议提供的ftp和http协议来访问文件
            
        魔术引号自动过滤magic_quotes_gpc = on
        magic_quotes_gpc = off 在php.ini中默认是关闭的,如果打开它,将自动把用户提交对sql的查询的语句进行转换,如果设置成ON,php会把所有的单引号,双引号,和反斜杠和空字符加上反斜杠进行转义
         
        外部程序执行目录safe_mode_exec_dir = "/usr/local/bin"
        当安全模式被激活，safe_mode_exec_dir参数限制通过exec()函数执行的可执行文件到指定的目录

0x03. 审计工具
        
        Seay源码审计；Fortify SCA ；RIPS等
        
