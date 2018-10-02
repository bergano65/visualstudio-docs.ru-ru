---
title: 'Практическое: создание. Vsct-файл из существующего. Файла ctc | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0d267e6046539001cbe454ab69867c02f0a606ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569776"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Практическое руководство. Создание файла VSCT на основе существующего файла CTC
Вы можете создать файл VSTC на основе XML из существующего исходного CTC-файла таблицы команд. Таким образом, можно воспользоваться преимуществами нового на базе XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] форматом компилятора таблицы (VSCT) команд.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC  
  
1.  Получите копию языка Perl.  
  
2.  Получите копию скрипта ConvertCTCToVSCT.pl, Perl, обычно находится в  *\<путь установки пакета SDK для Visual Studio >* \VisualStudioIntegration\Tools\bin папку.  
  
3.  Получите копию исходного файла CTC, который нужно преобразовать.  
  
4.  Поместите файлы в один каталог.  
  
5.  В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] окне командной строки, перейдите в каталог.  
  
6.  Тип  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Здесь PkgCmd.ctc — это имя файла CTC, а PkgCmd.vsct — имя файла VSCT, который нужно создать.  
  
     Будет создан исходный VSCT-файл таблицы команд XML. Этот файл можно скомпилировать с помощью Vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
    > [!NOTE]
    >  Чтобы повысить удобочитаемость файла VSCT, можно переформатировать комментарии XML.  
  
## <a name="see-also"></a>См. также  
 [Практическое: создание. Файл Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)