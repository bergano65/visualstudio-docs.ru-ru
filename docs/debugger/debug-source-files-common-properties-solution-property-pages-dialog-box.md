---
title: Отладка исходного файлы общих свойств, свойства страниц диалоговое окно решения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 844d189b9dd11945f4257b1fc9dfbd3117ac5199
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"
Эта страница свойств задает место, где отладчик будет осуществлять поиск исходных файлов при отладке решения.  
  
 Чтобы получить доступ к **исходные файлы отладки** страницу свойств, щелкните правой кнопкой мыши решение в **обозревателе решений** и выберите **свойства** в контекстном меню. Разверните **общие свойства** папку и нажмите кнопку **исходные файлы отладки** страницы.  
  
 **Каталоги, содержащие исходный код**  
 Список каталогов, в которых отладчик ищет исходные файлы при отладке решения. Поиск также производится внутри подкаталогов заданных каталогов.  
  
 **Не выполнять поиск следующих исходных файлов**  
 Введите имена файлов, которые отладчик не должен считывать. Если отладчик найдет один из этих файлов в одном из указанных каталогов, отладчик пропустит этот файл. Если **найти источник** появится диалоговое окно при отладке, и вы нажмете **отменить**, найден файл будет добавлен в этот список, отладчик прекратит поиск этого файла.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)