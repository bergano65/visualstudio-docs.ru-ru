---
title: Управление документами на сервере с помощью класса ServerDocument
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
ms.openlocfilehash: 97eed0e4cec143e51195347bfb90d430d8e1eadb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573002"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Управление документами на сервере с помощью класса ServerDocument
  Можно использовать `ServerDocument` в класс [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] для управления несколькими аспектами настроек уровня документа, даже если не установлено приложение Microsoft Office Word и Microsoft Office Excel. Можно выполнять следующие задачи:  
  
-   Просмотр и изменение данных в кэше данных документа или книги. Дополнительные сведения см. в разделе [работы с кэшированными данными в документе](#CachedData).  
  
-   Управление сборкой настройки, связанной с документом. Дополнительные сведения см. в разделе [Управление Настройка документа](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Понимать класса ServerDocument  
 `ServerDocument` Класс предназначен для использования на компьютерах, которые не установлен Office. Таким образом обычно используется этот класс в приложениях, не интегрированных с Microsoft Office, таких как проекты консольного или проекты Windows Forms, а не в проектах Office. Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса в *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* сборки.  
  
 `ServerDocument` Класс может использоваться для работы с настройками уровня документа, которые были созданы с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Дополнительные сведения о Visual Studio 2010 Tools для Office Runtime и расширения Office для платформы .NET Framework см. в разделе [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Если у вас есть устаревшие приложения, использующего `ServerDocument` класса в `Visual Studio Tools for Office` системы (версии 3.0 среды выполнения), `Visual Studio Tools for Office` система (среда выполнения версии 3.0) должна быть установлена на компьютерах под управлением приложения. `Visual Studio 2010 Tools for Office runtime` Не может запускать эти приложения.  
  
##  <a name="CachedData"></a> Работа с кэшированными данными в документе  
 `ServerDocument` Класс содержит члены, которые можно использовать для работы с кэшем данных в настроенных документах. Дополнительные сведения о кэшированных данных см. в разделе [данные кэша](../vsto/caching-data.md) и [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 В следующей таблице перечислены члены, которые можно использовать для работы с кэшированными данными.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, имеет ли документ кэш данных.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>;|  
|Для доступа к кэшированным данным в документе.<br /><br /> Дополнительные сведения см. в разделе [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Управление настройкой документа  
 Члены можно использовать `ServerDocument` класса для управления сборкой настройки, связанной с документом. Программным образом, удаление настройки из документа, чтобы документ больше не является частью настройки.  
  
 Ниже перечислены члены, которые можно использовать для управления сборки настройки.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, является ли документ является частью настройки уровня документа.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>;|  
|Для программного присоединения настройку в документ во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: присоединение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Один из <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> методы.|  
|Чтобы удалить из документа программными средствами настройки во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: Удаление управляемого кода расширения из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>;|  
|Чтобы получить URL-адрес манифеста развертывания, связанный с документом.|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>См. также  
 [Как: присоединение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Как: удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Кэширование данных](../vsto/caching-data.md)  
  