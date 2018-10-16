---
title: 'Практическое: создание. Vsct-файл из существующего. Руководитель технологического отдела компании файл | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 82cf711d33b3b3ca5150378e7111a2a21c8c03cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235746"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Практическое руководство. Создание файла VSCT на основе существующего файла CTO
Вы можете создать файл VSTC на основе XML из существующего двоичного CTO-файла. Это позволяет воспользоваться преимуществами нового формата компилятора таблицы команд. Этот процесс работает, даже если файл CTO был скомпилирован из файла CTC. Файл VSCT можно изменить и скомпилировать в другой файл CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Создание файла VSCT на основе файла CTO  
  
1.  Получите копии файла CTO и соответствующего файла CTSYM.  
  
2.  Поместите файлы в тот же каталог, что и компилятор vsct.exe.  
  
3.  В командной строке Visual Studio перейдите в каталог, содержащий файлы CTO и CTSYM.  
  
4.  Введите **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**.  
  
     `ctofilename` — это имя файла CTO, `vsctfilename` — имя файла VSCT, который нужно создать, а `symfilename` — имя файла CTSYM.  
  
     В результате этого процесса будет создан файл компилятора таблицы команд XML. Этот файл можно изменить и скомпилировать с помощью vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
## <a name="see-also"></a>См. также  
 [Практическое: создание. Файл Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)