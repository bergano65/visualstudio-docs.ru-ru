---
title: "Исходный код недоступен | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02c91f5e5a55e82633d89aa7209321126271e8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="no-source-available"></a>Исходный код недоступен
Проект не содержит исходного кода для кода, который вы пытаетесь просмотреть. Обычная причина — двойной щелчок модуля, который содержит исходный код в **окно стека вызовов** или **окно "Потоки"**. Можно продолжить отладку, но невозможно использовать окно с исходным кодом для установки точек останова и выполнения других действий в этом месте. Если вам нужно задать точку останова, используйте **Дизассемблированный** вместо него.  
  
 На страницах свойств решения можно поменять каталоги, в которых отладчик ищет исходные файлы, и указать отладчику пропускать выбранные исходные файлы. В разделе [отладки источника файлов, общих свойств, свойства страниц диалоговое окно решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Обзор для поиска исходного кода.**  
 Щелкните эту ссылку, чтобы открыть диалоговое окно, в котором можно просмотреть расположения и найти исходный код.  
  
 **Показывать Дизассемблированный код**  
 Запускает **Дизассемблированный**.  
  
 **Всегда показывать дизассемблированный код для отсутствующих исходных файлов**  
 Выберите этот параметр для отображения **Дизассемблированный** автоматически когда доступен без источника. Этот параметр может быть изменен в **параметры** диалоговом **Отладка** категории **Общие** страницы, установив или сняв **показывать дизассемблированный код, если не найден источник**.  
  
## <a name="see-also"></a>См. также  
 [Отладка исходного файлы общих свойств, решение диалоговом страниц свойств](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (расширение отладки SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)