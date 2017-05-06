---
title: "Практическое руководство. Программная защита документов и их частей"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "защита документов"
  - "документы [разработка решений Office в Visual Studio], защита документов"
  - "документы Word, защита"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Практическое руководство. Программная защита документов и их частей
  Вы можете добавлять защиту в документы Microsoft Office Word, чтобы запретить пользователям вносить изменения в документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Вы также можете помечать определенные части документа как исключения, чтобы указанные пользователи могли изменять только эти области документа. Например, можно защитить весь документ, кроме определенной закладки. При необходимости можно добавить пароль, чтобы пользователи, не знающие пароль, не могли удалить защиту документа.  
  
> [!NOTE]  
>  В следующем примере защита паролем не используется; однако вы можете рассмотреть возможность использования пароля при добавлении защиты документов. Дополнительные сведения см. в примере системы защиты документов по адресу [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Для защиты частей документов можно также использовать элементы управления содержимым. Для получения дополнительной информации см. [Практическое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Защита документа, который является частью настройки уровня документа  
  
#### Защита документа, который является частью настройки уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> класса `ThisDocument` в проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### Исключение элемента управления "Закладка" из защиты документа  
  
1.  Защитите весь документ при помощи метода <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  Исключите `Bookmark1` из защиты документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### Компиляция кода  
 Чтобы использовать эти примеры кода, выполняйте их из класса `ThisDocument` в своем проекте. В этих примерах кода предполагается, что элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> с именем `Bookmark1` существует в документе, в котором отображается этот код.  
  
## Защита документа с помощью надстройки VSTO  
  
#### Защита документа с помощью надстройки VSTO уровня приложения  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> документа <xref:Microsoft.Office.Interop.Word.Document>, который требуется защитить.  
  
     В следующем примере кода защищается активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Практическое руководство. Выполнение с выделенным кодом документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  