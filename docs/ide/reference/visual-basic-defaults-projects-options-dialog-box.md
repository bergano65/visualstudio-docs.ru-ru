---
title: "Страница &quot;Параметры Visual Basic по умолчанию&quot;, папка &quot;Проекты&quot;, диалоговое окно &quot;Параметры&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Оператор Option Explicit, настройка в IDE"
  - "Оператор Option Compare, настройка в IDE"
  - "Оператор Option Strict, настройка в IDE"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Страница &quot;Параметры Visual Basic по умолчанию&quot;, папка &quot;Проекты&quot;, диалоговое окно &quot;Параметры&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает настройки по умолчанию для параметров проекта Visual Basic.  При создании нового проекта указанные дополнительные операторы будут добавлены в заголовок проекта в редакторе кода.  Эти параметры применяются ко всем проектам Visual Basic.  
  
 Чтобы открыть это диалоговое окно, в меню **Сервис** выберите пункт **Параметры**, разверните папку **Проекты и решения** и щелкните **Параметры VB по умолчанию**.  
  
 **Option Explicit**  
 Задает значение компилятора по умолчанию, делающее явные объявления переменных обязательными.  По умолчанию параметр **Option Explicit** имеет значение **Вкл**.  Дополнительные сведения см. в разделе [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Задает значение компилятора по умолчанию, делающее явные сужающие преобразования обязательными, а позднее связывание недопустимым.  По умолчанию параметр **Option Strict** имеет значение **Выкл**.  Дополнительные сведения см. в разделе [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Задает значение компилятора по умолчанию для сравнения строк: двоичное \(с учетом регистра\) или текстовое \(без учета регистра\). По умолчанию параметр **Option Compare** имеет значение **Binary**.  Дополнительные сведения см. в разделе [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Устанавливается значение компилятор по умолчанию для локального определения типов.  По умолчанию параметр **Option Infer** имеет значение **Вкл.** для вновь созданных проектов и **Выкл.** для перенесенных проектов, которые были созданы в более ранних версиях языка Visual Basic.  Дополнительные сведения см. в разделе [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## См. также  
 [Проекты и решения](../../ide/solutions-and-projects-in-visual-studio.md)