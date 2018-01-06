---
title: "Безопасность решений SharePoint | Документы Microsoft"
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
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22ef16c40fb2d70ae7e1b835860b74843abe57d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="security-for-sharepoint-solutions"></a>Безопасность решений SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]включает в себя следующие возможности для повышения безопасности приложений SharePoint.  
  
## <a name="safe-control-entries"></a>Записи безопасных элементов управления  
 Каждый элемент проекта SharePoint, созданный в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] имеет **записи безопасных элементов управления** свойство, которое представляет безопасный коллекции элементов управления. Его **безопасном** вложенное свойство позволяет указать, безопасные элементы управления. Дополнительные сведения см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [указание безопасное веб-частей](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>Атрибут AllowPartiallyTrustedCallersAttribute  
 По умолчанию только приложения, которые являются полностью доверенными среды выполнения система безопасности доступа кода (CAS) можно получить доступ к общей сборке управляемого кода. Пометка в полностью доверенной сборке с атрибутом AllowPartiallyTrustedCallers позволяет частично доверенным сборкам для доступа к нему.  
  
 Атрибут AllowPartiallyTrustedCallers добавляется в любые решения SharePoint, не развернут для системы глобального кэша сборок ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Сюда входят изолированные решения или решения, развернутые в каталоге Bin приложения SharePoint. Дополнительные сведения см. в разделе [изменения системы безопасности версии 1 для Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) и [развертывание веб-частей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Безопасно в отношении скриптов  
 *Внедрение скрипта* представляет вставку потенциально вредоносный код в элементы управления или веб-страниц. Для защиты сайтов SharePoint 2010 от внедрения скрипта участники невозможно просматривать и изменять веб-частей и их свойствам по умолчанию. Это поведение контролируется с помощью атрибута SafeControl вызывается SafeAgainstScript. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], установите значение этого атрибута в элементе проекта **записи безопасных элементов управления** вложенное свойство **безопасен в отношении скриптов**. Дополнительные сведения см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [как: элементы управления пометить как безопасные элементы управления](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista и Windows 7 контроль учетных записей  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] встроенная функция безопасности управления учетных записей пользователей (UAC). Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] системах контроля учетных Записей необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системный администратор. Из **запустить** меню, откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем выберите **Запуск от имени администратора**.  
  
 Чтобы настроить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ярлык всегда Запуск от имени администратора, откройте ее контекстное меню, выберите **свойства**, выберите **Дополнительно** кнопку в **свойства**диалоговое окно, а затем выберите **Запуск от имени администратора** флажок.  
  
 Дополнительные сведения см. в разделе [понимание и настройка контроля учетных записей в Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). и [контроля учетных записей Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Разрешения безопасности SharePoint  
 Для разработки решений SharePoint, необходимо иметь достаточные разрешения на выполнение и отладку решений SharePoint. Перед началом тестирования решения SharePoint, выполните следующие действия, чтобы убедиться, что имеются необходимые разрешения.  
  
1.  Добавление учетной записи пользователя с правами администратора в системе.  
  
2.  Добавление учетной записи пользователя как администратора фермы на сервере SharePoint.  
  
    1.  В центре администрирования SharePoint 2010 выберите **управление группой администраторов фермы** ссылку.  
  
    2.  На **Администраторы фермы** выберите **New** пункта меню  
  
3.  Добавить вашу учетную запись пользователя в группу WSS_ADMIN_WPG.  
  
## <a name="additional-security-resources"></a>Дополнительные ресурсы по безопасности  
 Дополнительные сведения о проблемах безопасности см. в следующих.  
  
### <a name="visual-studio-security"></a>Безопасность Visual Studio  
  
-   [Безопасность и разрешения пользователя](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Безопасность в машинный код и код .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Безопасность в .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>Безопасности SharePoint  
  
-   [SharePoint Foundation администрирования и безопасности](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Центр ресурсов безопасности SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Обеспечение безопасности веб-частей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Улучшение безопасности веб-приложений: Угрозы и меры противодействия](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Общая безопасность  
  
-   [Жизненного цикла разработки безопасности MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Разработка безопасных приложений ASP.NET: Проверка подлинности, авторизации и безопасного обмена данными](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  