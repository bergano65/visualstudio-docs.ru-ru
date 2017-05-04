---
title: "Управление документами на сервере с помощью класса ServerDocument | Microsoft Docs"
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
helpviewer_keywords: 
  - "документы [разработка решений Office в Visual Studio], управление на сервере"
  - "Office - документы [разработка решений Office в Visual Studio], управление на сервере"
  - "ServerDocument - класс, управление документами на сервере"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Управление документами на сервере с помощью класса ServerDocument
  Для управления некоторыми аспектами настроек уровня документа можно использовать класс ServerDocument в среде [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], даже на сервере не установлены Microsoft Office Word и Microsoft Office Excel.  На этом занятии можно выполнить следующие задачи.  
  
-   Получение доступа к данным и изменение данных в кэше данных документа или рабочей книги.  Дополнительные сведения см. в разделе [Работа с кэшированными данными в документе](#CachedData).  
  
-   Управление сборкой настройки, связанной с документом.  Дополнительные сведения см. в разделе [Управление настройкой документа](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Основные сведения о классе ServerDocument  
 Класс ServerDocument разработан для использования на компьютерах, на которых не установлен Microsoft Office.  Поэтому этот класс используется в приложениях, не интегрированных с Office, например, в консольных проектах или проектах Windows Forms, но не в проектах Office.  Используйте класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> в сборке Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 Класс ServerDocument можно использовать, чтобы работать с настройки уровня документа, созданные с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Дополнительные сведения о средствах Visual Studio 2010 для выполнения office и расширения office для платформы .NET Framework см. в разделе [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Если приложение прежних версий, которое использует класс ServerDocument в Visual Studio Tools для системы Microsoft office \(версия 3.0\), выполнения Visual Studio Tools для системы Microsoft office \(выполнения версии 3.0\) должен устанавливаться на компьютерах, работающих под управлением приложение.  Средства Visual Studio 2010 для выполнения office нельзя выполнять эти приложения.  
  
##  <a name="CachedData"></a> Работа с кэшированными данными в документе  
 Класс ServerDocument предоставляет члены, которые можно использовать для работы с кэшем данных в настроенных документах.  Дополнительные сведения о кэшированных данных см. в разделах [Кэширование данных](../vsto/caching-data.md) и [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 В следующей таблице перечислены методы, используемые для работы с кэшированными данными.  
  
|Задача|Используемые члены класса|  
|------------|-------------------------------|  
|Чтобы определить наличие в документе кэша данных|Метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Получение доступа к кэшированным данным в документе.<br /><br /> Для получения дополнительной информации см. [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Управление настройкой документа  
 Можно использовать члены класса ServerDocument для управления сборкой настройки, связанной с этим документом.  Например, можно программными средствами удалить настройку из документа, таким образом он перестанет быть частью настройки.  
  
 В следующей таблице перечислены методы, используемые для управления сборкой настройки.  
  
|Задача|Используемые члены класса|  
|------------|-------------------------------|  
|Чтобы определить, является ли документ частью настройки уровня документа|Метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Прикрепление настройки к документу программным способом во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md).|Один из методов <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.|  
|Удаление настройки из документа программным способом во время выполнения.<br /><br /> Для получения дополнительной информации см. [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Получение URL\-адреса манифеста развертывания, связанного с документом, и его изменение.|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## См. также  
 [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Кэширование данных](../vsto/caching-data.md)  
  
  