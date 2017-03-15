---
title: "Практическое руководство. Создание файла VSCT на основе существующего файла CTC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "файлы VSCT, создание на основе файла CTC"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Практическое руководство. Создание файла VSCT на основе существующего файла CTC
Вы можете создать файл VSTC на основе XML из существующего исходного CTC\-файла таблицы команд. Таким образом можно воспользоваться новым форматом компилятора таблицы команд [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] на основе XML \(VSCT\).  
  
### Создание файла VSCT на основе файла CTC  
  
1.  Получите копию языка Perl.  
  
2.  Получите копию скрипта ConvertCTCToVSCT.pl на языке Perl, который обычно находится в папке *\<путь установки пакета SDK для Visual Studio\>*\\VisualStudioIntegration\\Tools\\bin.  
  
3.  Получите копию исходного файла CTC, который нужно преобразовать.  
  
4.  Поместите файлы в один каталог.  
  
5.  В окне командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] перейдите в этот каталог.  
  
6.  Тип  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Здесь PkgCmd.ctc — это имя файла CTC, а PkgCmd.vsct — имя файла VSCT, который нужно создать.  
  
     Будет создан исходный VSCT\-файл таблицы команд XML. Этот файл можно скомпилировать с помощью Vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
    > [!NOTE]
    >  Чтобы повысить удобочитаемость файла VSCT, можно переформатировать комментарии XML.  
  
## См. также  
 [Практическое руководство: создание. Файл Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)