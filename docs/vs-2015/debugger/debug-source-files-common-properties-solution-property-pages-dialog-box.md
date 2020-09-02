---
title: Исходные файлы отладки, диалоговое окно "Общие свойства", страницы свойств решения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143033"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница свойств задает место, где отладчик будет осуществлять поиск исходных файлов при отладке решения.  
  
 Чтобы зайти на страницу свойств **Исходные файлы отладки**, щелкните правой кнопкой мыши решение в окне **Обозреватель решений**, а затем выберите пункт **Свойства** в меню быстрого вызова. Разверните папку **Общие свойства** и выберите страницу **Исходные файлы отладки**.  
  
 **Каталоги, содержащие исходный код**  
 Список каталогов, в которых отладчик ищет исходные файлы при отладке решения. Поиск также производится внутри подкаталогов заданных каталогов.  
  
 **Не выполнять поиск следующих исходных файлов**  
 Введите имена файлов, которые отладчик не должен считывать. Если отладчик найдет один из этих файлов в одном из указанных каталогов, отладчик пропустит этот файл. Если во время отладки появится диалоговое окно **Поиск исходного текста** и вы нажмете **Отмена**, искомый файл будет добавлен к этому списку, и отладчик прекратит поиск этого файла.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
