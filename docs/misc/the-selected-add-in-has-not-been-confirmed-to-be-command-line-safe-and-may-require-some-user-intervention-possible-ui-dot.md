---
title: "The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI). | Microsoft Docs"
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
  - "vs.message.0x800A0031"
  - "vs.message.VB_E_IDWADDINCMDLINE"
ms.assetid: 19dd24d4-b0f5-4c92-9005-aad48ffda7d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI).
Эта ошибка обычно возникает, когда надстройка была выбрана для использования из командной строки \(DOS\), но не перечисляется как безопасная для командной строки.  Надстройка может отображать пользовательский интерфейс, мешающий использованию командной строки.  
  
### Чтобы исправить эту ошибку  
  
1.  В меню **Сервис** выберите пункт **Диспетчер надстроек**.  
  
2.  В диалоговом окне **Диспетчер надстроек** снимите флажок **Командная строка** для этой надстройки.  
  
## См. также  
 [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md)   
 [Практическое руководство. Создание надстройки](../Topic/How%20to:%20Create%20an%20Add-In.md)