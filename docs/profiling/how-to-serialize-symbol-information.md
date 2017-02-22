---
title: "Практическое руководство. Сериализация сведений о символах | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "средства профилирования, сериализация сведений о символах"
  - "средства повышения производительности, сериализация сведений о символах"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Сериализация сведений о символах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно выполнить сериализацию символов, необходимых для анализа работы приложения.  При сериализации символы добавляются в VSP\-файл.  Благодаря добавлению сведений о символах в VSP\-файл другие пользователи могут анализировать отчет о производительности, не обращаясь к исходным символам.  Если символы не сериализованы, для анализа VSP\-файла потребуются исходные инструментированные EXE\- и PDB\-файлы.  
  
### Автоматическая сериализация сведений о символах  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
     Откроется диалоговое окно **Параметры**.  
  
2.  Выберите **Средства производительности**.  
  
3.  В разделе **Общие параметры** установите флажок **Автоматическая сериализация символьной информации**.  
  
## См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/ru-ru/0340ddde-caf4-48ac-8af3-d15dcdade556)