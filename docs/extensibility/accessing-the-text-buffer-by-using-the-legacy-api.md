---
title: "Доступ к буфер текста с помощью API прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77002e095690da85e73f1a79d405cb5174b96851
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Доступ к буфер текста с помощью API прежних версий
Текст отвечает за управление текстовыми потоками и сохранения файла. Несмотря на то, что буфер могли читать или записывать другие форматы, весь обычный обмен данными с помощью буфера выполняется с использованием кодировки Юникод. В прежних версий API-интерфейсы буфер текста можно использовать одно - или двумерной системе координат для обозначения расположений символа в буфере.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Один и два измерения координации систем  
 Одномерный массив координат позиции основан на позицию символа с первого символа в буфере, например 147. Вы используете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейс для доступа к одномерный расположение в буфере. Двумерной системе координат основана на пары строки и индекс. Например символ в буфере, с 43 5 будет находиться на строке 43, пять знаков справа от первого символа в этой строке. Доступ двухмерный расположение в буфере с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейса. Как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы, реализуемые объект текстового буфера (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) и могут быть доступны друг от друга с помощью `QueryInterface`. На следующей диаграмме показан на эти и другие интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Объект текстового буфера](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Объект текстового буфера  
  
 Несмотря на то, что либо системы координат работает в буфере, он оптимизированы для использования двумерные координаты. Одномерный массив координатной системы можно создать снижение производительности. Поэтому используйте двумерной системе координат, когда это возможно.  
  
 Текст буфера второй ответственности — файл сохраняемости. Чтобы сделать это, реализующий объект текстового буфера <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и выступает в качестве компонента объекта данных документа для элементов проекта и другие компоненты среды, участвующие в сохраняемости. Дополнительные сведения см. в разделе [открытия и сохранения элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Объясняется, как изменить параметры представления с помощью предыдущих версий API.  
  
 [С помощью диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Содержит сведения об использовании диспетчера текстов для наблюдения за глобальные параметры...  
  
## <a name="see-also"></a>См. также  
 [В редакторе Core](../extensibility/inside-the-core-editor.md)