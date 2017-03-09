---
title: "Имя &quot;&lt;имя&gt;&quot; не объявлено или не находится в текущей области | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36610"
  - "bc36610"
helpviewer_keywords: 
  - "BC36610"
ms.assetid: e66a4b8a-9252-42ae-a30d-341fad4f74be
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Имя &quot;&lt;имя&gt;&quot; не объявлено или не находится в текущей области
Запрос LINQ ссылается на программный элемент, но компилятор не может найти элемент с указанным именем.  
  
 **Идентификатор ошибки:** BC36610  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания в ссылающемся операторе. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не учитывается регистр, но любое другое изменение в орфографии дает другое имя. Обратите внимание, что символ подчеркивания \(`_`\) является частью имени и, следовательно, частью орфографии.  
  
2.  Убедитесь, что программный элемент находится в области. Если ссылающийся оператор находится вне области объявления программного элемента, может потребоваться уточнение имени элемента. Для получения дополнительной информации см. [Область видимости в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/scope).  
  
3.  Убедитесь, что между объектом и его членами имеется оператор доступа к членам \(`.`\). Например, если у вас есть элемент управления <xref:System.Windows.Forms.TextBox> с именем `TextBox1`, то для доступа к его свойству <xref:System.Windows.Forms.TextBoxBase.Text%2A> следует ввести `TextBox1.Text`. Если вместо этого ввести `TextBox1Text`, будет создано другое имя.  
  
## См. также  
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Соглашения об именах Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [Ссылки на объявленные элементы](/dotnet/visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements)