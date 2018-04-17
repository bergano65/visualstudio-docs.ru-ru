---
title: Управление документами на сервере с помощью класса ServerDocument | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef676de4ff352a557019f68037203364a97834d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Managing Documents on a Server by Using the ServerDocument Class
  Можно использовать в класса ServerDocument [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] для управления несколькими аспектами настроек уровня документа, даже если не установлено приложение Microsoft Office Word и Microsoft Office Excel. Можно выполнять следующие задачи:  
  
-   Просмотр и изменение данных в кэше данных документа или книги. Дополнительные сведения см. в разделе [работа с кэшированные данные в документе](#CachedData).  
  
-   Управление сборкой настройки, связанной с документом. Дополнительные сведения см. в разделе [Управление настройкой документа](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Основные сведения о класса ServerDocument  
 Класс ServerDocument предназначен для использования на компьютерах, которые не установлен Office. Таким образом обычно используется этот класс в приложениях, не интегрированных с Microsoft Office, таких как проекты консольного или проекты Windows Forms, а не в проектах Office. Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса в сборке Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 Можно использовать для работы с настройками уровня документа, которые были созданы с помощью класса ServerDocument [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Дополнительные сведения о Visual Studio 2010 Tools для Office Runtime и расширения Office для платформы .NET Framework см. в разделе [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  При наличии устаревшего приложения, использующего класса ServerDocument в Visual Studio Tools для системы Microsoft Office (версия 3.0 среды выполнения), Visual Studio Tools для системы Microsoft Office (версии 3.0 среды выполнения) должен устанавливаться на компьютерах под управлением приложения. Средства Visual Studio 2010 для Office Runtime не может запускать эти приложения.  
  
##  <a name="CachedData"></a> Работа с кэшированными данными в документе  
 Класса ServerDocument содержит члены, которые можно использовать для работы с кэшем данных в настроенных документах. Дополнительные сведения о кэшированных данных см. в разделе [кэширование данных](../vsto/caching-data.md) и [доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 В следующей таблице перечислены члены, которые можно использовать для работы с кэшированными данными.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, имеет ли документ кэш данных.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>;|  
|Для доступа к кэшированным данным в документе.<br /><br /> Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Управление настройкой документа  
 Члены класса ServerDocument можно использовать для управления сборкой настройки, связанной с документом. Программным образом, удаление настройки из документа, чтобы документ больше не является частью настройки.  
  
 Ниже перечислены члены, которые можно использовать для управления сборки настройки.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, является ли документ является частью настройки уровня документа.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>;|  
|Для программного присоединения настройку в документ во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: присоединение управляемых расширений кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Один из <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> методы.|  
|Чтобы удалить из документа программными средствами настройки во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: удаление управляемых расширений кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>;|  
|Чтобы получить URL-адрес манифеста развертывания, связанный с документом.|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>См. также  
 [Как: вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Как: удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Кэширование данных](../vsto/caching-data.md)  
  