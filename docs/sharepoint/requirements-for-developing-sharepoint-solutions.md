---
title: "Требования по разработке решений SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, необходимые компоненты"
  - "разработка приложений SharePoint в Visual Studio, требования"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Требования по разработке решений SharePoint
  Чтобы использовать средства разработки решений SharePoint, входящие в состав Visual Studio, в системе должны быть установлены следующие компоненты.  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] или выпуск Visual Studio Application Lifecycle Management \(ALM\).  
  
    -   Компонент [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] или [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] \(или оба\) при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] на 64\-разрядной версии [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64\-разрядной версии [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
     или  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] на 64\-разрядной версии [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64\-разрядной версии [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
> [!NOTE]  
>  Хотя формально SharePoint поддерживает только серверные операционные системы, две клиентские операционные системы разрешены. [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] и [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1.  Дополнительные сведения в разделе [Руководство по установке станции разработки SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Для проектов типа модели подключения к бизнес\-данным требуется наличие [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] в системе.  
  
 Для разработки решений SharePoint в необходимо установить SharePoint на одном компьютере с Visual Studio.  Кроме того, средства разработки SharePoint поддерживают только изолированную конфигурацию; конфигурация фермы не поддерживается.  
  
> [!NOTE]  
>  Проекты SharePoint в Visual Studio поддерживают только [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  Если для нового проекта SharePoint выбирается [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)], целевой все равно остается [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Дополнительные сведения об установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] см. в разделе [Установка Visual Studio](../Topic/Installing%20Visual%20Studio.md).  
  
## Управление учетными записями в Vista и Windows 7  
 В [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] имеется встроенная функция обеспечения безопасности — управление учетными записями или UAC.  Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в системах [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] UAC требует запуска [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] от имени системного администратора.  На рабочем столе вызовите контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и выберите команду **Запуск от имени администратора**.  
  
 Можно настроить ярлык на рабочем столе так, чтобы приложение всегда запускалось от имени администратора. Для этого щелкните ярлык правой кнопкой мыши, выберите пункт **Свойства**, нажмите кнопку **Дополнительно** и выберите флажок **Запуск от имени администратора**.  
  
 Дополнительные сведения см. в [Контроль учетных записей в Windows Vista: общие сведения и настройка](http://go.microsoft.com/fwlink/?LinkID=156476) и [Windows Vista: контроль учетных записей пользователей](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Замечания о разрешениях для SharePoint  
 Для разработки решений SharePoint необходимо иметь соответствующие разрешения для их запуска и отладки.  Прежде чем тестировать решение SharePoint, выполните следующие действия, чтобы обеспечить наличие необходимых разрешений.  
  
1.  Добавьте свою учетную запись в систему в качестве учетной записи администратора.  
  
2.  Добавьте свою учетную запись на сервер SharePoint в качестве учетной записи администратора фермы.  
  
    1.  В центре администрирования SharePoint щелкните ссылку **Управление группой администраторов фермы**.  
  
    2.  На странице **Администраторы фермы**, нажмите кнопку **Создать**.  
  
3.  Добавьте свою учетную запись в группу WSS\_ADMIN\_WPG.  
  
## См. также  
 [Начало работы &#40;разработка решений SharePoint в Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  