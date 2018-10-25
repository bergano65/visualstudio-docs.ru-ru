---
title: Безопасность решений SharePoint | Документация Майкрософт
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
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b014c3b4ada42982c41928ca17472e3f585af3ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878769"
---
# <a name="security-for-sharepoint-solutions"></a>Безопасность решений SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] включает в себя следующие функции для повышения безопасности приложений SharePoint.

## <a name="safe-control-entries"></a>Записи безопасных элементов управления
 Каждый элемент проекта SharePoint, созданный в [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] имеет **записи безопасных элементов управления** свойство, которое представляет безопасный коллекции элементов управления. Его **безопасном** вложенное свойство позволяет указать элементы управления безопасные. Дополнительные сведения см. в разделе [сведениями развертывание пакетов и в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [Specifying Safe Web Parts](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>Атрибут AllowPartiallyTrustedCallers
 По умолчанию только приложения, полностью доверенной для среды выполнения система безопасности доступа кода (CAS) можно получить доступ к общей сборке управляемого кода. Пометка полностью доверенной сборке с атрибутом AllowPartiallyTrustedCallers позволяет частично доверенным сборкам для доступа к нему.

 Атрибут AllowPartiallyTrustedCallers добавляется любое решение SharePoint, не развертывается в системе глобальный кэш сборок ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Сюда входят изолированные решения или решения, развернутые в каталоге Bin приложения SharePoint. Дополнительные сведения см. в разделе [Version 1 Security Changes для Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) и [развертывание веб-частей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Безопасен в отношении скриптов
 *Скрипт путем внедрения кода* — это Вставка потенциально вредоносного кода в элементы управления или веб-страниц. Для защиты сайтов SharePoint 2010 от внедрение скриптов участниками нельзя просматривать или изменять веб-частей и их свойствам по умолчанию. Это поведение управляется SafeControl атрибут с именем SafeAgainstScript. В [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], задайте этот атрибут в элементе проекта **записи безопасных элементов управления** подсвойств **безопасен в отношении скриптов**. Дополнительные сведения см. в разделе [сведениями развертывание пакетов и в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [как: Пометка элементов управления как безопасных](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Vista и Windows 7 контроля учетных записей
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] встроенная функция безопасности контроля учетных записей (UAC). Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] системах контроля учетных Записей необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системным администратором. Из **запустить** меню, откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем выберите **Запуск от имени администратора**.

 Чтобы настроить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ярлык, чтобы всегда Запуск от имени администратора, откройте его контекстное меню, выберите **свойства**, выберите **Дополнительно** кнопку **свойства**диалоговое окно, а затем выберите **Запуск от имени администратора** "флажок".

 Дополнительные сведения см. в разделе [понимание и настройка контроля учетных записей в Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). и [контроль учетных записей пользователей Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Разрешения безопасности SharePoint
 Для разработки решений SharePoint, необходимо иметь достаточные разрешения для запуска и отладки решений SharePoint. Перед тестированием решения SharePoint, выполните следующие действия, чтобы убедиться, что имеются необходимые разрешения.

1.  Добавьте учетную запись пользователя с правами администратора в системе.

2.  Добавьте учетную запись пользователя как администратора фермы на сервере SharePoint.

    1.  В центре администрирования SharePoint 2010 выберите **управление группой администраторов фермы** ссылку.

    2.  На **Администраторы фермы** выберите **New** пункт меню

3.  Добавить вашу учетную запись пользователя в группу WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Дополнительные материалы по безопасности
 Дополнительные сведения о проблемах безопасности см. в разделе ниже.

### <a name="visual-studio-security"></a>безопасность Visual Studio

-   [Безопасность и разрешения пользователей](http://go.microsoft.com/fwlink/?LinkId=177503)

-   [Безопасность в машинном коде и коде .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)

-   [Безопасность в .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>Безопасность SharePoint

-   [Администрирование SharePoint Foundation и безопасность](http://go.microsoft.com/fwlink/?LinkId=177501)

-   [Центр ресурсов безопасности SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)

-   [Защита веб-частей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

-   [Повышение безопасности веб-приложений: Угрозы и меры противодействия](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Общая безопасность

-   [Жизненный цикл разработки безопасности MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)

-   [Разработка безопасных приложений ASP.NET: Проверка подлинности, авторизации и безопасный обмен данными](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>См. также

- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)