---
title: Исходный код недоступен | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9213abc9dab5824422b0fadf3920ffb188ab14
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266088"
---
# <a name="no-source-available"></a>Исходный код недоступен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Проект не содержит исходного кода для кода, который вы пытаетесь просмотреть. Обычная причина — двойной щелчок модуля, который не содержит исходный код в **Call Stack Window** или **окна "Потоки"**. Можно продолжить отладку, но невозможно использовать окно с исходным кодом для установки точек останова и выполнения других действий в этом месте. Если вам нужно установить точку останова, используйте **Дизассемблированный** вместо этого.  
  
 На страницах свойств решения можно поменять каталоги, в которых отладчик ищет исходные файлы, и указать отладчику пропускать выбранные исходные файлы. См. в разделе [отладка диалоговое окно страниц свойств источника файлы, общие свойства решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Обзор для поиска исходного кода**  
 Щелкните эту ссылку, чтобы открыть диалоговое окно, в котором можно просмотреть расположения и найти исходный код.  
  
 **Показывать Дизассемблированный код**  
 Запускает **Дизассемблированный**.  
  
 **Всегда показывать дизассемблированный код для отсутствующих исходных файлов**  
 Выберите этот параметр для отображения **Дизассемблированный** автоматически когда доступна без источника. Этот параметр может быть изменен в **параметры** диалоговом окне **Отладка** категории **Общие** страницы, установив или сняв **показывать дизассемблированный код, если исходный код недоступен**.  
  
## <a name="see-also"></a>См. также  
 [Отладка диалоговое окно страниц свойств источника файлы, общие свойства решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (расширение отладки SOS)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)



