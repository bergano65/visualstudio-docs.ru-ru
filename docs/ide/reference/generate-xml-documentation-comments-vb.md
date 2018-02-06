---
title: "Создание комментариев XML-документации для Visual Basic | Документация Майкрософт"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Создание комментариев XML-документации в Visual Basic

**Что?** Вы можете сразу же создавать основной XML-файл, который требуется для документирования выбранного элемента. 

**Когда?** Если необходимо создать комментарии XML-документации для последующей обработки средством документации, например Sandcastle.

**Зачем?** Вы можете сами вручную создать все примечания, но эта возможность позволяет сэкономить время и повысить точность благодаря созданию базового шаблона и дополнительных элементов. 

**Как?**

1. Поместите текстовый курсор над элементом, например методом, который нужно задокументировать.

   ![Метод для документирования](media/doc-highlight-vb.png)

1. Затем введите **'''** (3 одиночные кавычки), после чего будет автоматически создан базовый шаблон и дополнительные элементы, если необходимо.  Например, при комментировании метода будут созданы теги **\<summary\>** и **\<param\>** для каждого параметра, который передается в метод, а также тег **\<returns\>**, чтобы задокументировать результат, возвращаемый методом.

   ![Шаблон](media/doc-preview-vb.png)

1. Введите комментарии и добавьте дополнительную информацию, которую вы считаете нужной.

   ![Ввод комментариев](media/doc-result-vb.png)

## <a name="see-also"></a>См. также

[Документирование кода с помощью XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Создание кода](../code-generation-in-visual-studio.md)