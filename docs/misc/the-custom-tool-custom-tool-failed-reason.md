---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
Настраиваемый инструмент не был успешно запущен.  
  
 Если при обновлении проектов, содержащих N\-уровневые наборы данных, возникает ошибка MSDataSetGenerator, необходимо повторно запустить настраиваемое средство после обновления всех проектов.  
  
 Не удалось запустить настраиваемое средство "MSDataSetGenerator".  Проект, указанный в атрибуте DataSetProject в поле \<dataset name\>, должен быть ориентирован на версию платформы .NET Framework, равную или превышающую версию текущего проекта.  
  
### Исправление ошибок MSDataSetGenerator в N\-уровневых наборах данных  
  
-   В обозревателе решений щелкните файл XSD правой кнопкой мыши и выберите команду **Запустить пользовательский инструмент**.