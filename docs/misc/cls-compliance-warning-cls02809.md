---
title: "Предупреждение о соответствии CLS CLS02809 | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии CLS CLS02809
Свойства должны следовать определенному шаблону именования  
  
 Свойства должны следовать определенному шаблону именования: имя функции доступа свойства будет таким же, как и имя свойства, но с добавлением префикса **get\_** или **set\_**.  
  
 Атрибут **specialname** должен игнорироваться в соответствующих сравнениях имен и соответствовать правилам в отношении идентификаторов.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении функции \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS02809:  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 Обратите внимание на то, что имена методов доступа отличаются от имени свойства.  Чтобы устранить предупреждение CLS02809, обеспечьте соответствие имен всех свойств шаблону именования.