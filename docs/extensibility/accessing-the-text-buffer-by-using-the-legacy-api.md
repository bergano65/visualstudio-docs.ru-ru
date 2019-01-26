---
title: Доступ к текстовый буфер с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dfd4535eb0d792e323143bdebd4b5e17a048e1d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972671"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Доступ к текстового буфера, используя старый API
Текст отвечает за управление текстовыми потоками и сохраняемость файлов. Несмотря на то, что буфер можно считывать или записывать другие форматы, весь обычный обмен данными с буфером выполняется с помощью Юникода. В устаревшие API-интерфейсы текстовый буфер можно использовать одно - или двумерной системе координат для обозначения расположений символов в буфере.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Один и два измерения координации систем  
 Одномерный массив координат положения основан на позицию символа с первого символа в буфере, например 147. Использовании <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейс для доступа к одномерный местом в буфере. В двумерной системе координат основан на строки и индекса пары. Например символ в буфере, с 43 5 будет находиться в строке 43, пять символов справа от первого символа в этой строке. Доступ двухмерный расположение в буфере с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс. Как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы реализуемые объект текстового буфера (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) и может быть организован друг с другом с помощью `QueryInterface`. В приведенной ниже схеме показано этих и других ключевых интерфейсов <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Объект текстового буфера](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Объект текстового буфера  
  
 Несмотря на то, что любой из систем координат работает в текстовом буфере, он оптимизирован для использования двухмерные координаты. Одномерный массив системы координат можно создать снижению производительности. Таким образом используйте двумерной системе координат, когда это возможно.  
  
 Текст буфера второй ответственности является сохранение состояния файла. Чтобы сделать это, реализующий объект текстового буфера <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и выступает в качестве компонента объекта данных документа для элементов проекта и другие компоненты среды, участвующие в сохраняемости. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Изменение параметров представления с помощью предыдущих версий API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 В этой статье описывается изменение параметров представления, с помощью предыдущих версий API.  
  
 [Использование диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 В этой статье описывается использование диспетчера текстов для наблюдения за глобальные параметры.  
  
## <a name="see-also"></a>См. также  
 [В редакторе](../extensibility/inside-the-core-editor.md)