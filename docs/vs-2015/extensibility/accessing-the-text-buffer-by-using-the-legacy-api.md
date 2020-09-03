---
title: Доступ к текстовому буферу с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185014"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Доступ к текстовому буферу с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текст отвечает за управление текстовыми потоками и сохранением файлов. Хотя буфер может считывать или записывать другие форматы, все обычные соединения с буфером выполняются с помощью Юникода. В интерфейсах API прежних версий текстовый буфер может использовать одну или двухмерную систему координат для обнаружения расположений символов в буфере.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Системы координат с одним и двумя измерениями  
 Координата одномерной координаты основана на позиции символа из первого символа в буфере, например 147. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>Интерфейс используется для доступа к одномерному расположению в буфере. Двухмерная система координат основана на парах строк и индексов. Например, символ в буфере в 43, 5 будет в строке 43, пять символов справа от первого символа в этой строке. Доступ к многомерному расположению в буфере осуществляется с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейса. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>И <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы реализуются объектом текстового буфера ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ), и к ним можно получить доступ друг от друга с помощью `QueryInterface` . На следующей схеме показаны эти и другие ключевые интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Объект текстового буфера](../extensibility/media/vstextbuffer.gif "встекстбуффер")  
Объект текстового буфера  
  
 Хотя какая-либо система координат работает в текстовом буфере, она оптимизирована для использования двумерных координат. Одномерный система координат может создавать накладные расходы на производительность. Поэтому, когда это возможно, используйте двухмерную систему координат.  
  
 Второй обязанностью текстового буфера является сохранение файлов. Для этого объект текстового буфера реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и действует как компонент объекта данных документа для элементов проекта и других компонентов среды, участвующих в сохраняемости. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Объясняет, как изменить параметры представления с помощью API прежних версий.  
  
 [Использование диспетчера текстов для мониторинга глобальных параметров](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Описание использования диспетчера текста для мониторинга глобальных параметров...  
  
## <a name="see-also"></a>См. также:  
 [Компоненты основного редактора](../extensibility/inside-the-core-editor.md)
