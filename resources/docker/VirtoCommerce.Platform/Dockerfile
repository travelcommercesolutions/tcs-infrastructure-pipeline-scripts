# escape=`

FROM microsoft/aspnet:4.7.2
MAINTAINER Alexander Siniouguine <support@virtocommerce.com>

ARG SOURCE=VirtoCommerce.Platform

ADD $SOURCE c:\vc-platform

# Configure website
RUN Remove-Website -Name 'Default Web Site'; `  
    md c:\vc-platform\App_Data\Assets; `
    md C:\vc-platform\App_Data\Modules; `
    md C:\vc-platform\Modules; `
    New-Website -Name 'vc-platform' `
                -Port 80 -PhysicalPath 'c:\vc-platform' `
                -ApplicationPool 'DefaultAppPool'

RUN c:\windows\system32\inetsrv\appcmd add vdir "/app.name:'vc-platform/'" /path:/assets /physicalPath:c:\vc-platform\app_data\assets; `
    icacls C:\inetpub\wwwroot\App_Data /t /grant "Users:W"; `
    icacls C:\inetpub\wwwroot\Modules /t /grant "Users":W;