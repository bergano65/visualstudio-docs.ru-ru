---
title: Определение пространства имен по умолчанию для проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705774"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Определение пространства имен по умолчанию для проекта
[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Если `CustomToolNamespace` свойство задано для входного файла, то значение `CustomToolNamespace` становится значением параметра пространства имен по умолчанию, переданного <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> методу. В противном случае `wszDefaultNamespace` параметр, передаваемый в, `Generate` всегда равен корневому пространству имен. Дополнительные сведения о пространствах имен см. в разделе [Ключевые слова пространства имен](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] использует пространства имен на основе папок. Это значит, что пространство имен состоит из корневого пространства имен, а также имен всех папок, содержащих пользовательский инструмент. Имя каждой папки преобразуется в допустимый идентификатор, а точки разделяются на все имена. Например, если входной файл FolderA\FolderB\FolderC\MyInput.txt, а корневое пространство имен — CL9, то вычисленное пространство имен по умолчанию будет **CL9. Папка a. Фолдерб. Фолдерк**.  
  
 Исключением из этого правила является ситуация, когда цепочка иерархии содержит папку веб-ссылок. Например, если:  
  
- Фолдерк является папкой веб-ссылок, пространством имен было бы **CL9. Фолдерк**.  
  
- Фолдерб является папкой веб-ссылок, пространством имен было бы **CL9. Фолдерб. Фолдерк**.  
  
  Это значит, что пространство имен использует следующий формат:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>См. также:  
 [Реализация генераторов с одним файлом](../extensibility/internals/implementing-single-file-generators.md)   
 [Регистрация генераторов одного файла](../extensibility/internals/registering-single-file-generators.md)   
 [Предоставление типов конструкторам визуальных элементов](../extensibility/internals/exposing-types-to-visual-designers.md)