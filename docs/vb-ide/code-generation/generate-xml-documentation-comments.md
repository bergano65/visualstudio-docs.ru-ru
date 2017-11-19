---
title: "Создавать комментарии XML-документации - формирования кода (Visual Basic) | Документы Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1291667c7acb47abe543d275549179abea0c8467
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Создавать комментарии XML-документации в Visual Basic
**Что:** позволяет сразу создавать базовый XML требуется для документирования выбранного элемента. 

**Когда:** необходимо создать для последующей обработки средствами документации как Sandcastle комментариев XML-документа.

**Почему:** можно вручную создать блок комментариев всей самостоятельно, однако это сэкономит время и повысить точность путем создания базовый шаблон и дополнительные элементы. 

**Как:**

1. Поместите курсор над элементом, для документов, например, метод текста.

   ![Метод документ](media/doc_highlight.png)

1. Затем введите **'''** (3 одиночные кавычки) который автоматически создает базовый шаблон и любые дополнительные элементы при необходимости.  Например, при создании комментариев к методу, он создает  **\<сводки\>**  тегов, а также  **\<param\>**  тег для каждого параметра, который является передается в метод и  **\<возвращает\>**  тег для документирования, метод возвращает.

   ![Шаблон](media/doc_preview.png)

1. Завершите комментарии и добавить дополнительную информацию, которую вы считаете, что не требуется.

   ![Завершенная комментария](media/doc_result.png)

## <a name="see-also"></a>См. также
[Документирование кода с помощью XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Создание кода (Visual Basic)](../code-generation-vb.md) 