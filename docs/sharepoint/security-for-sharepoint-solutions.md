---
title: Безопасность для решений SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc1449a40528670274ea5b275cca3f0a8d2f277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983779"
---
# <a name="security-for-sharepoint-solutions"></a>Безопасность для решений SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] включает следующие функции, помогающие повысить безопасность приложений SharePoint.

## <a name="safe-control-entries"></a>Записи безопасного контроля
 Каждый элемент проекта SharePoint, созданный в [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] , имеет свойство **записи безопасного элемента управления** , представляющее коллекцию безэлементных элементов управления. Его **безопасное** подсвойство позволяет указать элементы управления, которые вы считаете безопасными. Дополнительные сведения см. [в разделе Предоставление сведений о пакете и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [Указание безопасного веб-части](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>атрибут AllowPartiallyTrustedCallersAttribute
 По умолчанию только приложения, полностью доверенные системой управления доступом для кода среды выполнения (CAS), могут получить доступ к общей сборке управляемого кода. Пометка полностью доверенной сборки атрибутом AllowPartiallyTrustedCallers позволяет сборкам с частичным доверием обращаться к ней.

 Атрибут AllowPartiallyTrustedCallers добавляется в любое решение SharePoint, которое не развернуто в глобальном кэше сборок ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Сюда входят изолированные решения или решения, развернутые в каталоге Bin приложения SharePoint. Дополнительные сведения см. в статье [изменения системы безопасности версии 1 для платформы Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) и [Развертывание веб-части в SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Безопасность в отношении свойства скрипта
 *Внедрение сценариев* — это вставка потенциально вредоносного кода в элементы управления или веб-страницы. Для защиты сайтов SharePoint 2010 от внедрения скриптов участники не могут просматривать или изменять веб-части или их свойства по умолчанию. Это поведение управляется атрибутом SafeControl с именем Сафеагаинстскрипт. В [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] присвойте этому атрибуту в подсвойстве **записей безопасного элемента** проекта, **защищенном от скрипта**. Дополнительные сведения см. [в разделе Предоставление сведений о пакете и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [Пометка элементов управления как безэлементных элементов управления](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Контроль учетных записей пользователей Vista и Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] включают функцию безопасности, известную как управление учетными записями пользователей (UAC). Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] системах система UAC требует использования учетной записи [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системного администратора. В меню **Пуск** откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и выберите команду **Запуск от имени администратора**.

 Чтобы настроить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ярлык всегда запускать от имени администратора, откройте его контекстное меню, выберите пункт **свойства**, нажмите кнопку **Дополнительно** в диалоговом окне **Свойства** , а затем установите флажок **Запуск от имени администратора** .

 Дополнительные сведения см. [в разделе понимание и настройка контроля учетных записей в Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). и [Управление учетными записями пользователей Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Рекомендации по разрешениям SharePoint
 Для разработки решений SharePoint необходимо иметь достаточные разрешения для выполнения и отладки решений SharePoint. Прежде чем можно будет протестировать решение SharePoint, выполните следующие действия, чтобы убедиться в наличии необходимых разрешений.

1. Добавьте учетную запись пользователя в качестве администратора в системе.

2. Добавьте учетную запись пользователя в качестве администратора фермы для сервера SharePoint.

    1. В центре администрирования SharePoint 2010 выберите ссылку **Управление группой администраторов фермы** .

    2. На странице **Администраторы фермы** выберите пункт **создать** меню.

3. Добавьте учетную запись пользователя в группу WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Дополнительные ресурсы со сведениями об обеспечении безопасности
 Дополнительные сведения о проблемах безопасности см. в следующих статьях.

### <a name="visual-studio-security"></a>безопасность Visual Studio

- [Безопасность и разрешения пользователей](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Безопасность в машинном коде и коде .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Безопасность в .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Безопасность SharePoint

- [Администрирование и безопасность SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Центр ресурсов безопасности SharePoint](/sharepoint/dev/)

- [Обеспечение безопасности веб-части в SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Повышение безопасности веб-приложений: угрозы и контрмеры](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Общая безопасность

- [Жизненный цикл разработки системы безопасности MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Создание безопасных приложений ASP.NET: проверка подлинности, авторизация и безопасное взаимодействие](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>См. также раздел

- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)