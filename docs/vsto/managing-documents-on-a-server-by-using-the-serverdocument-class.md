---
title: Управление документами на сервере с помощью класса ServerDocument
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 739946fc7fc6ea7014fb93010ca85094a7fc7056
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251936"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Управление документами на сервере с помощью класса ServerDocument
  `ServerDocument` Класс в можно использовать дляуправлениянесколькимиаспектаминастроекнауровнедокумента,дажееслиMicrosoftOfficeWordиMicrosoftOfficeExcelнеустановлены.[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Вы можете выполнять следующие задачи:

- Доступ к данным и их изменение в кэше данных документа или книги. Дополнительные сведения см. [в разделе Работа с кэшированными данными в документе](#CachedData).

- Управление сборкой настройки, связанной с документом. Дополнительные сведения см. [в разделе Управление настройкой документа](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Общие сведения о классе ServerDocument
 `ServerDocument` Класс предназначен для использования на компьютерах, на которых не установлен Office. Таким образом, этот класс обычно используется в приложениях, которые не интегрируются с Office, например в консольных проектах или проектах Windows Forms, а не в проектах Office. Используйте класс в сборке *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll.* <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>

 Класс можно использовать для выполнения настроек на уровне документа, созданных с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. `ServerDocument`

 Дополнительные сведения о среде выполнения Visual Studio 2010 Tools for Office и расширениях Office для .NET Framework см. в разделе [Общие сведения о инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Если у вас есть устаревшее приложение, использующее `ServerDocument` класс `Visual Studio Tools for Office` в системе (версия `Visual Studio Tools for Office` 3,0 runtime), система (среда выполнения версии 3,0) должна быть установлена на компьютерах, на которых выполняется приложение. `Visual Studio 2010 Tools for Office runtime` Не удается запустить эти приложения.

## <a name="CachedData"></a>Работа с кэшированными данными в документе
 `ServerDocument` Класс предоставляет элементы, которые можно использовать для работы с кэшем данных в пользовательских документах. Дополнительные сведения о кэшированных данных см. в разделе [кэширование данных](../vsto/caching-data.md) и [доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).

 В следующей таблице перечислены элементы, которые можно использовать для работы с кэшированными данными.

|Задача|Используемый член|
|----------|-------------------|
|Чтобы определить, имеется ли в документе кэш данных.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> ;|
|Для доступа к кэшированным данным в документе.<br /><br /> Дополнительные сведения см. [в разделе доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|

## <a name="CustomizationInfo"></a>Управление настройкой документа
 Члены `ServerDocument` класса можно использовать для управления сборкой настройки, связанной с документом. Например, можно программно удалить настройку из документа, чтобы документ больше не был частью настройки.

 В следующей таблице перечислены элементы, которые можно использовать для управления сборкой настройки.

|Задача|Используемый член|
|----------|-------------------|
|Для определения того, является ли документ частью настройки уровня документа.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> ;|
|Для программного присоединения настройки к документу во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [Практическое руководство. Присоединение расширений управляемого кода к документам](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Один из <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> методов.|
|Программное удаление настройки из документа во время выполнения.<br /><br /> Дополнительные сведения см. в разделе [Практическое руководство. Удаление расширений управляемого кода из](../vsto/how-to-remove-managed-code-extensions-from-documents.md)документов.|метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> ;|
|Для получения URL-адреса манифеста развертывания, связанного с документом.|Свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|

## <a name="see-also"></a>См. также
- [Практическое руководство. Присоединение расширений управляемого кода к документам](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Общие сведения о Инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Кэширование данных](../vsto/caching-data.md)
