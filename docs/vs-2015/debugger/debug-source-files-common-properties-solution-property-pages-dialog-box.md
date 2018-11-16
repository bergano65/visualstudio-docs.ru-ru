---
title: Отладка диалоговое окно страниц свойств источника файлы, общие свойства решения | Документация Майкрософт
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
manager: ghogen
ms.openlocfilehash: 84bf975065d73cd2d25994855a4c8a236f706e3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744672"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта страница свойств задает место, где отладчик будет осуществлять поиск исходных файлов при отладке решения.  
  
 Чтобы получить доступ к **исходные файлы отладки** страницу свойств, щелкните правой кнопкой мыши решение в **обозревателе решений** и выберите **свойства** в контекстном меню. Разверните **общие свойства** папку и нажмите кнопку **исходные файлы отладки** страницы.  
  
 **Каталоги, содержащие исходный код**  
 Список каталогов, в которых отладчик ищет исходные файлы при отладке решения. Поиск также производится внутри подкаталогов заданных каталогов.  
  
 **Не выполнять поиск следующих исходных файлов**  
 Введите имена файлов, которые отладчик не должен считывать. Если отладчик найдет один из этих файлов в одном из указанных каталогов, отладчик пропустит этот файл. Если **найти источник** появится диалоговое окно во время отладки, и вы нажмете **отменить**, искомый файл добавляется в этот список, чтобы отладчик прекратит поиск этого файла.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)



