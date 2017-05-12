---
title: "Безопасность решений SharePoint"
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
  - "безопасность [SharePoint development in Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, безопасность"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Безопасность решений SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] содержит следующие компоненты, помогающие повысить уровень безопасности приложений SharePoint.  
  
## Записи безопасных элементов управления  
 Каждый элемент проекта SharePoint, созданный в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] имеет свойство **Записи безопасных элементов управления**, представляющее коллекцию безопасных элементов управления.  Его вложенное свойство **Безопасность** позволяет указать безопасные элементы управления.  Дополнительные сведения см. в [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [Указание безопасных веб\-частей](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## Атрибут AllowPartiallyTrustedCallers  
 По умолчанию только загружаемые из среды выполнения приложения, обладающие полным уровнем доверия системы управления доступом для кода \(CAS\) могут получить доступ к общей сборке управляемого кода.  Маркировка полностью доверенной сборки с помощью атрибута AllowPartiallyTrustedCallers разрешает доступ к ней частично доверенным сборкам.  
  
 Атрибут AllowPartiallyTrustedCallers добавлен в любое решение SharePoint, которое не развернуто в системе глобальных кэш сборок \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  Сюда включаются обезвреженные решения или решения, развернутые в каталоге Bin приложения SharePoint.  Дополнительные сведения см. в [Изменения системы безопасности для Microsoft .NET Framework. Версия 1](http://go.microsoft.com/fwlink/?LinkId=177515) и [Развертывание веб\-частей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Свойство "Безопасно в отношении скриптов"  
 *Внедрение скрипта* представляет собой вставку в элементы управления или веб\-страницы потенциально вредоносного кода.  Для защиты сайтов SharePoint 2010 от вставки скрипта, участники не могут просматривать или править веб\-страницы или свойства, заданные по умолчанию.  Такое поведение контролируется атрибутом SafeControl, вызываемым SafeAgainstScript.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] установите этот атрибут для элемента проекта **Записи безопасных элементов управления** во вложенном свойстве **Безопасно в отношении скриптов**.  Дополнительные сведения см. в разделах [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) и [Практическое руководство. Пометка элементов управления как безопасных](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Управление учетными записями пользователей в Windows Vista и Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] имеют встроенную функцию управления безопасностью, называемую контролем учетных записей.  Для разработки решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в системах [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] и [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], контроль учетных записей требует запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] от имени системного администратора.  Из меню **Пуск** откройте контекстное меню для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а затем выберите **Запуск от имени администратора**.  
  
 Чтобы настроить ярлык [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] так, чтобы приложение всегда запускалось от имени администратора, необходимо открыть его контекстное меню, выбрать пункт **Свойства**, выбрать кнопку **Дополнительно** в диалоговом окне **Свойства**, а затем выбрать флажок **Запуск от имени администратора**.  
  
 Дополнительные сведения см. в [Контроль учетных записей в Windows Vista: общие сведения и настройка](http://go.microsoft.com/fwlink/?LinkID=156476) и [Windows Vista: контроль учетных записей пользователей](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Замечания о разрешениях для SharePoint  
 Для разработки решений SharePoint необходимо иметь соответствующие разрешения для их запуска и отладки.  Прежде чем тестировать решение SharePoint, выполните следующие действия, чтобы обеспечить наличие необходимых разрешений.  
  
1.  Добавьте свою учетную запись в систему в качестве учетной записи администратора.  
  
2.  Добавьте свою учетную запись на сервер SharePoint в качестве учетной записи администратора фермы.  
  
    1.  В центре администрирования SharePoint 2010 выберите ссылку **Управление группой администраторов фермы**.  
  
    2.  На странице **Администраторы фермы**, выберите пункт меню **Создать**  
  
3.  Добавьте свою учетную запись в группу WSS\_ADMIN\_WPG.  
  
## Дополнительные ресурсы безопасности  
 Для получения дополнительных сведений по вопросам безопасности см. следующие разделы.  
  
### Безопасность Visual Studio  
  
-   [Безопасность и предоставленные пользователям разрешения](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Безопасность в машинном коде и коде .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Безопасность в .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### Безопасность SharePoint  
  
-   [Безопасность в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Центр ресурсов безопасности SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Защита веб\-частей в службах SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Улучшение безопасности веб\-приложений: Improving Web Application Security: угрозы и противодействие](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### Общая безопасность  
  
-   [Жизненный цикл безопасной разработки Microsoft \(SDL\)](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Сборка безопасных приложений ASP.NET: проверка подлинности, авторизация и безопасная коммуникация](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  