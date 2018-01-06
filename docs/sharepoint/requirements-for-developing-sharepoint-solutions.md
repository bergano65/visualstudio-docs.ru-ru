---
title: "Требования по разработке решений SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a32ceee7609fca96f27388839415ec5ac4d219de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Требования по разработке решений SharePoint
  Перед тем как использовать средства разработки решений SharePoint, входящих в Visual Studio, необходимо установить следующие компоненты в системе:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]или выпуск из Visual Studio Application Lifecycle Management (ALM).  
  
    -   Либо [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] или [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] функцию (или оба) при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]установлен в 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
     или  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]установлен в 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
> [!NOTE]  
>  Хотя формально SharePoint поддерживает только серверные операционные системы, допускаются две клиентские операционные системы: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] и [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] с пакетом обновления 1. Дополнительные сведения см. в разделе [установки SharePoint Server 2010 Developer рабочей станции руководство](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Бизнес-данным (BDC) модели проекта типов требуют [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] установлено в системе.  
  
 Для разработки решений SharePoint в Visual Studio, необходимо установить SharePoint на одном компьютере с Visual Studio. Кроме того средства разработки SharePoint поддерживают только изолированную конфигурацию SharePoint; они не поддерживают конфигурации фермы (удаленном).  
  
> [!NOTE]  
>  Проекты SharePoint в Visual Studio поддерживают только [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. При выборе [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] для нового проекта SharePoint, будут по-прежнему связаны [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Дополнительные сведения об установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], в разделе [установите Visual Studio](../install/install-visual-studio.md).  
  
## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista и контроль учетных (записей UAC) в Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] встроенная функция безопасности, известный как элемент управления учетных записей пользователей (UAC). Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] системах контроля учетных Записей необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системный администратор. На рабочем столе откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем выберите **Запуск от имени администратора**.  
  
 Чтобы настроить ярлыка на рабочем столе, чтобы приложение всегда запускалось от имени администратора, откройте ее контекстное меню, выберите **свойства**, выберите **Дополнительно** и затем выберите **Запуск от имени администратора**  флажок.  
  
 Дополнительные сведения см. в разделе [понимание и настройка контроля учетных записей в Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). и [контроля учетных записей Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Разрешения безопасности SharePoint  
 Для разработки решений SharePoint, необходимо иметь достаточные разрешения на выполнение и отладку решений SharePoint. Перед началом тестирования решения SharePoint, выполните следующие действия, чтобы убедиться, что имеются необходимые разрешения.  
  
1.  Добавление учетной записи пользователя с правами администратора в системе.  
  
2.  Добавление учетной записи пользователя как администратора фермы на сервере SharePoint.  
  
    1.  В центре администрирования SharePoint выберите **управление группой администраторов фермы** ссылку.  
  
    2.  На **Администраторы фермы** выберите **New** кнопки.  
  
3.  Добавить вашу учетную запись пользователя в группу WSS_ADMIN_WPG.  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе &#40; Разработка приложений SharePoint в Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  