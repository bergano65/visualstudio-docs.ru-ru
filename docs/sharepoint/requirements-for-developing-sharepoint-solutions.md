---
title: Требования по разработке решений SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9d6a726b290bfed1c086f9fb03290a37c91490
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119401"
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Требования по разработке решений SharePoint
Перед тем как использовать средства разработки решений SharePoint, входящих в Visual Studio, необходимо установить следующие компоненты в системе:

- Visual Studio с C# или Visual Basic или выпуск из Visual Studio Application Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] установлен в 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     или

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] установлен в 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] или 64-разрядной [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Хотя формально SharePoint поддерживает только серверные операционные системы, допускаются две клиентские операционные системы: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] и [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] с пакетом обновления 1. Дополнительные сведения см. в разделе [SharePoint Server 2010 Developer рабочей станции руководства](http://go.microsoft.com/fwlink/?LinkID=164557).

Типов проектов бизнес-модели подключения к данным (BDC) требуют [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] установлены в системе.

Для разработки решений SharePoint в Visual Studio, необходимо установить SharePoint на одном компьютере с Visual Studio. Кроме того средства разработчика SharePoint поддерживают только изолированную конфигурацию SharePoint; они не поддерживают конфигурации фермы (удаленно).

> [!NOTE]
> Проекты SharePoint в Visual Studio поддерживают только [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. При выборе [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] для нового проекта SharePoint, он будет по-прежнему ориентироваться [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Дополнительные сведения об установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], см. в разделе [установка Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista и контроль учетных (записей UAC) Windows 7
[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] встроенная функция безопасности, который известен как контроля учетных записей (UAC). Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] системах контроля учетных Записей необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системным администратором. На рабочем столе, откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем выберите **Запуск от имени администратора**.

Чтобы настроить ярлыка на рабочем столе, чтобы всегда выполнять от имени администратора, откройте его контекстное меню, выберите **свойства**, выберите **Дополнительно** и затем выберите **Запуск от имени администратора**  "флажок".

Дополнительные сведения см. в разделе [понимание и настройка контроля учетных записей в Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). и [контроль учетных записей пользователей Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Разрешения безопасности SharePoint
Для разработки решений SharePoint, необходимо иметь достаточные разрешения для запуска и отладки решений SharePoint. Перед тестированием решения SharePoint, выполните следующие действия, чтобы убедиться, что имеются необходимые разрешения.

1. Добавьте учетную запись пользователя с правами администратора в системе.

2. Добавьте учетную запись пользователя как администратора фермы на сервере SharePoint.

    1. В центре администрирования SharePoint выберите **управление группой администраторов фермы** ссылку.

    2. На **Администраторы фермы** выберите **New** кнопки.

3. Добавить вашу учетную запись пользователя в группу WSS_ADMIN_WPG.

## <a name="see-also"></a>См. также
[Начало работы &#40;разработка приложений SharePoint в Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
