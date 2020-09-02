---
title: Нет доступных источников | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697799"
---
# <a name="no-source-available"></a>Исходный код недоступен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Проект не содержит исходного кода для кода, который вы пытаетесь просмотреть. Обычно это происходит, когда в окне **Стек вызовов** или **Потоки** производится двойной щелчок по модулю, который не имеет исходного кода. Можно продолжить отладку, но невозможно использовать окно с исходным кодом для установки точек останова и выполнения других действий в этом месте. Если необходимо установить точку останова, следует использовать **окно дизассемблирования**.  
  
 На страницах свойств решения можно поменять каталоги, в которых отладчик ищет исходные файлы, и указать отладчику пропускать выбранные исходные файлы. См. [страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно страниц свойств решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Обзор для поиска исходного кода**  
 Щелкните эту ссылку, чтобы открыть диалоговое окно, в котором можно просмотреть расположения и найти исходный код.  
  
 **Показать дизассемблированный код**  
 Запускает **окно дизассемблирования**.  
  
 **Всегда показывать дизассемблированный код для отсутствующих исходных файлов**  
 Установите этот параметр, чтобы **окно дизассемблирования** открывалось автоматически при отсутствии исходного кода. Этот параметр также можно изменить в диалоговом окне **Параметры** (категория **Отладка**, страница **Общие**), установив или сняв флажок **Показывать дизассемблированный код, если исходный код недоступен**.  
  
## <a name="see-also"></a>См. также:  
 [Исходные файлы отладки, диалоговое окно "Общие свойства", страницы свойств решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Указание символов (. pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (расширение отладки SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
