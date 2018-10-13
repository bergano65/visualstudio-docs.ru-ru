---
title: Представление Windows | Документация Майкрософт
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
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4622e268aaaf76a2968a2bc6ef67ead7b0c45b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261707"
---
# <a name="windows-view"></a>Представление окон
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При первом открытии Spy ++, представление Windows дерево всех окон и элементов управления в системе. Отображаются имя дескриптора и класс окна. Текущее окно рабочего стола — в верхней части дерева. Все остальные окна являются дочерними элементами рабочего стола и перечислены в соответствии с иерархией стандартное окно. Дочерние окна отображаются в раскрывающихся списках под их родительские элементы.  
  
 На следующем рисунке показано типичное представление Spy ++ Windows с развернутым верхним узлом.  
  
 ![Spy&#43; &#43; представление Windows](../debugger/media/spy-windowsview.png "Spy ++ _WindowsView")  
Представление окон в Spy++  
  
 Текущее окно рабочего стола — в верхней части дерева. Все остальные окна являются дочерними элементами рабочего стола, а также перечислены в соответствии с иерархией стандартное окно, с помощью того же уровня windows, упорядоченных по Z-порядка. Можно развернуть или свернуть, щелкнув любой родительский узел дерева + или - символ рядом с узлом.  
  
 Если фокус находится представление Windows, можно использовать инструмент поиска в [диалоговое окно "Поиск окна"](../debugger/window-search-dialog-box.md) для отображения сведений в любом окне open в вашей системе.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Использование инструмента поиска](../debugger/how-to-use-the-finder-tool.md)  
 Показывает, как это средство проверки окон для свойства или сообщения.  
  
 [Практическое руководство. Поиск окна в представлении окон](../debugger/how-to-search-for-a-window-in-windows-view.md)  
 Описание способов поиска отдельного окна в представлении Windows.  
  
 [Практическое: отображение свойств окна](../debugger/how-to-display-window-properties.md) m  
 Процедуры для открытия диалогового окна "Свойства окна".  
  
## <a name="related-sections"></a>Связанные разделы  
 [Представления Spy++](../debugger/spy-increment-views.md)  
 Описание представления дерева Spy ++ окон, сообщений, процессов и потоков.  
  
 [Использование Spy++](../debugger/using-spy-increment.md)  
 Представлены средства Spy ++ и рассказывается, как он может использоваться.  
  
 [Диалоговое окно "Поиск окна"](../debugger/find-window-dialog-box.md)  
 Используется для просмотра свойств или сообщений из отдельного окна.  
  
 [Диалоговое окно "Поиск окна"](../debugger/window-search-dialog-box.md)  
 Используется для поиска узла для отдельного окна в представлении Windows.  
  
 [Диалоговое окно "Свойства окна"](../debugger/window-properties-dialog-box.md)  
 Используется для отображения свойств окна, выбранного в представлении Windows.  
  
 [Справочник по Spy++](../debugger/spy-increment-reference.md)  
 Содержит разделы, описывающие каждый Spy ++ меню и диалоговое окно.



