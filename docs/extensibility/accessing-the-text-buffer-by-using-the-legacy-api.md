---
title: Доступ к текстовый буфер с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661bf39e82fef5c040861bc9386dcb7f897d25cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313629"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Доступ к текстового буфера, используя старый API
Текст отвечает за управление текстовыми потоками и сохраняемость файлов. Несмотря на то, что буфер можно считывать или записывать другие форматы, весь обычный обмен данными с буфером выполняется с помощью Юникода. В устаревшие API-интерфейсы текстовый буфер можно использовать одно - или двумерной системе координат для обозначения расположений символов в буфере.

## <a name="one--and-two-dimension-coordinate-systems"></a>Один и два измерения координации систем
 Одномерный массив координат положения основан на позицию символа с первого символа в буфере, например 147. Использовании <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейс для доступа к одномерный местом в буфере. В двумерной системе координат основан на строки и индекса пары. Например символ в буфере, с 43 5 будет находиться в строке 43, пять символов справа от первого символа в этой строке. Доступ двухмерный расположение в буфере с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс. Как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы реализуемые объект текстового буфера (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) и может быть организован друг с другом с помощью `QueryInterface`. В приведенной ниже схеме показано этих и других ключевых интерфейсов <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![Объект текстового буфера](../extensibility/media/vstextbuffer.gif "vsTextBuffer") объект текстового буфера

 Несмотря на то, что любой из систем координат работает в текстовом буфере, он оптимизирован для использования двухмерные координаты. Одномерный массив системы координат можно создать снижению производительности. Таким образом используйте двумерной системе координат, когда это возможно.

 Текст буфера второй ответственности является сохранение состояния файла. Чтобы сделать это, реализующий объект текстового буфера <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и выступает в качестве компонента объекта данных документа для элементов проекта и другие компоненты среды, участвующие в сохраняемости. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>Содержание раздела
- [Изменить параметры представления, используя старый API](../extensibility/changing-view-settings-by-using-the-legacy-api.md) объясняется, как изменить параметры представления, используя старый API.

- [Использование диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md) содержит сведения об использовании диспетчера текстов для наблюдения за глобальные параметры.

## <a name="see-also"></a>См. также
- [В редакторе](../extensibility/inside-the-core-editor.md)