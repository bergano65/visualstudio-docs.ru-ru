---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
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
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
Не удается найти предоставленный операционной системой файл DLL, например DDEML.DLL, VERSION.DLL или WINSPOOL.DRV.  Эта ошибка обычно возникает, если выполняется одно из следующих условий: файл отсутствует в соответствующем каталоге, DLL была повреждена или удалена либо недостаточно памяти.  
  
### Чтобы исправить эту ошибку  
  
1.  Проверьте, что DLL находится в системном каталоге Windows.  
  
     —или—  
  
     Перегрузите DLL.  
  
     —или—  
  
     Попытайтесь освободить память, закрыв другие открытые приложения.