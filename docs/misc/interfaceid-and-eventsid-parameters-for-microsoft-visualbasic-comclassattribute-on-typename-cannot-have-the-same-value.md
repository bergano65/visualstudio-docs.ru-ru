---
title: "Значения параметров InterfaceId и EventsId для Microsoft.VisualBasic.ComClassAttribute в &quot;&lt;имя_типа&gt;&quot; не могут совпадать | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Значения параметров InterfaceId и EventsId для Microsoft.VisualBasic.ComClassAttribute в &quot;&lt;имя_типа&gt;&quot; не могут совпадать
В блоке атрибутов `COMClassAttribute` для интерфейса и для события создания задан один и тот же идентификатор GUID. Если указаны оба идентификатора, то они должны различаться. Они также должны отличаться от идентификатора класса.  
  
 Идентификатор GUID состоит из 16 байтов, первые восемь из которых являются числовыми, а последние восемь — двоичными. Он создается служебными программами Майкрософт, например uuidgen.exe, и поэтому его уникальность гарантируется.  
  
 **Идентификатор ошибки:** BC32507  
  
### Исправление ошибки  
  
1.  Определите правильные идентификаторы GUID, необходимые для идентификации интерфейса и события создания COM\-объекта.  
  
2.  Убедитесь в том, что строки GUID, представленные в блоке атрибутов `COMClassAttribute`, скопированы правильно.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)