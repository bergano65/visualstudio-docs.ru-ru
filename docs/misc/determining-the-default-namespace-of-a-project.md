---
title: "Определение пространства имен по умолчанию для проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пользовательские инструменты, вычисление пространства имен по умолчанию"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Определение пространства имен по умолчанию для проекта
Для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>, если  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]свойство устанавливается во входном файле, затем значении  `CustomToolNamespace` преобразуется в значение параметра пространства имен по умолчанию, переданного  `CustomToolNamespace` метод.  В противном случае \- `wszDefaultNamespace` параметр, передаваемый  `Generate` всегда равны к корневому пространству имен.  Дополнительные сведения о пространствах имен см. в разделе [Ключевые слова, используемые для пространств имен](/dotnet/csharp/language-reference/keywords/namespace-keywords).  
  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] использует папка\-основанные пространства имен.  Это значит, что пространства имен состоит из корневого пространства имен и имена всех папок, содержащий пользовательское средство.  Каждая папка с именами преобразована в допустимый идентификатор и точки разделяют все имена.  Например, если входной файл FolderC \\ FolderA \\ FolderB \\ MyInput.txt и корневое пространство имен CL9, вычисленный по умолчанию пространство имен было бы **CL9.FolderA.FolderB.FolderC**.  
  
 Исключением из этого правила являются происходит, когда цепочку иерархии содержит папку веб\-ссылка.  Например, если:  
  
-   FolderC было папке веб\-ссылка, пространство имен будет **CL9.FolderC**.  
  
-   FolderB было папке веб\-ссылка, пространство имен будет **CL9.FolderB.FolderC**.  
  
 Это значит, что пространства имен используется следующий формат:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## См. также  
 [Реализация генераторов одного файла](../extensibility/internals/implementing-single-file-generators.md)   
 [Регистрация генераторов одного файла](../extensibility/internals/registering-single-file-generators.md)   
 [Предоставление визуальные конструкторы типов](../extensibility/internals/exposing-types-to-visual-designers.md)