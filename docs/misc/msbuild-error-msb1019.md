---
title: "Ошибка MSBuild MSB1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1019
**Неправильно сформирован ключ средства ведения журнала.**  
  
 Ключ **\/logger** указан неправильно.  Чтобы задать средство ведения журнала, необходимо указать хотя бы сборку этого средства, а чтобы явно задать конкретное средство ведения журнала для загрузки, укажите и класс средства, и его сборку.  Параметры средства ведения журнала не являются обязательными.  
  
### Чтобы исправить эту ошибку  
  
1.  Задайте средство ведения журнала, указав его класс и сборку.  Синтаксис `<logger>`:  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     Синтаксис `<logger class>`:  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     Синтаксис `<logger assembly>`:  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` задавать необязательно; параметры передаются в средство ведения журнала в точности так, как они введены.  
  
     Пример: \/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Средства ведения журнала построения](../msbuild/build-loggers.md)