---
title: Определение пространства имен по умолчанию проекта | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 27919985c09356764533e736899dc6a7cb5d0090
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560004"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Определение пространства имен по умолчанию для проекта
Для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], если `CustomToolNamespace` входного файла, то значение параметра установлено свойство `CustomToolNamespace` становится значением параметра пространство имен по умолчанию, передаваемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод. В противном случае `wszDefaultNamespace` параметр, передаваемый `Generate` всегда равно корневое пространство имен. Дополнительные сведения о пространствах имен см. в разделе [ключевые слова пространства имен](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] использует пространства имен на основе папок. То есть пространство имен состоит из корневого пространства имен, а также имена папкам, содержащим пользовательский инструмент. Каждое имя папки преобразуется в допустимый идентификатор и периоды разделения всех имен. Например, если входной файл является FolderA\FolderB\FolderC\MyInput.txt и корневым пространством имен является CL9, предпочтительным пространством имен по умолчанию вычисляемый **CL9. FolderA.FolderB.FolderC**.  
  
 Исключением из этого правила происходит, когда цепи иерархии содержит ссылку в веб-папку. Например если:  
  
-   FolderC были ссылку в веб-папку, пространство имен будет **CL9. FolderC**.  
  
-   FolderB были ссылку в веб-папку, пространство имен будет **CL9. FolderB.FolderC**.  
  
 То есть пространство имен используется следующий формат:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>См. также  
 [Реализация генераторов одного файла](../extensibility/internals/implementing-single-file-generators.md)   
 [Регистрация генераторов одного файла](../extensibility/internals/registering-single-file-generators.md)   
 [Предоставление типов конструкторам визуальных элементов](../extensibility/internals/exposing-types-to-visual-designers.md)