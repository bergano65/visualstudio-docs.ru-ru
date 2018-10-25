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
ms.openlocfilehash: e983f4cf1b90150113fcfa33702d85bb41a30924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939141"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Управление документами на сервере с помощью класса ServerDocument
  Можно использовать `ServerDocument` в класс [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] для управления несколькими аспектами настроек уровня документа, даже если не установлен Microsoft Office Word и Microsoft Office Excel. Можно выполнять следующие задачи:  
  
- Доступ и изменение данных в кэше данных документа или книги. Дополнительные сведения см. в разделе [работы с кэшированными данными в документе](#CachedData).  
  
- Управление сборкой настройки, связанной с документом. Дополнительные сведения см. в разделе [управление настройки документа](#CustomizationInfo).  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Узнайте класс ServerDocument  
 `ServerDocument` Класс предназначен для использования на компьютерах, которые не установлен Office. Таким образом обычно используется этот класс в приложениях, которые не интегрируются с Microsoft Office, такие как консольные проекты или проекты Windows Forms, а не в проектах Office. Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> в класс *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* сборки.  
  
 `ServerDocument` Класс может использоваться для работы в настройках уровня документа, которые были созданы с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Дополнительные сведения о Visual Studio 2010 Tools для Office Runtime и расширения Office для платформы .NET Framework, см. в разделе [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Если у вас есть на устаревшие приложения, использующего `ServerDocument` в класс `Visual Studio Tools for Office` системы (версии 3.0 среды выполнения), `Visual Studio Tools for Office` система (среда выполнения версии 3.0) должна быть установлена на компьютерах под управлением приложения. `Visual Studio 2010 Tools for Office runtime` Не может запускать эти приложения.  
  
##  <a name="CachedData"></a> Работа с кэшированными данными в документе  
 `ServerDocument` Класс предоставляет члены, которые можно использовать для работы с кэшем данных в настроенных документах. Дополнительные сведения о кэшированных данных, см. в разделе [кэшировать данные](../vsto/caching-data.md) и [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Ниже перечислены элементы, которые можно использовать для работы с кэшированными данными.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, является ли документ имеет кэш данных.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> ;|  
|Для доступа к кэшированным данным в документе.<br /><br /> Дополнительные сведения см. в разделе [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Управление настройки документа  
 Можно использовать члены `ServerDocument` класса для управления сборкой настройки, связанной с документом. Например можно программным способом удалить настройку из документа, чтобы документ больше не является частью настройки.  
  
 Ниже перечислены элементы, которые можно использовать для управления сборки настройки.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Чтобы определить, является ли документ является частью настройки уровня документа.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> ;|  
|Чтобы программным способом добавить настройку в документ во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: присоединение расширения управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Один из <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> методы.|  
|Чтобы программно удалить настройку из документа во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [как: Удаление управляемого кода расширения из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> ;|  
|Чтобы получить URL-адрес манифеста развертывания, связанный с документом.|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>См. также  
 [Практическое: присоединение расширения управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Практическое: удаление расширения управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Кэширование данных](../vsto/caching-data.md)  
  