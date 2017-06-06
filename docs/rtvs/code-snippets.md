---
title: "Фрагменты кода в инструментах R для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: ru-ru
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>Фрагменты кода

Фрагменты кода в Visual Studio позволяют быстро вставлять блоки кода произвольной длины, помогая избежать повторного ввода одинакового кода снова и снова. В инструментах R для Visual Studio (RTVS) имеется множество полезных фрагментов кода R, которые дополняют коллекцию фрагментов кода Visual Studio.

Чтобы вставить фрагмент, введите сокращенное название фрагмента (поддерживается технология IntelliSense), а затем нажмите клавишу TAB для вставки.

Вот несколько простых примеров.

- Введите `=`, затем нажмите клавишу TAB, после чего RTVS предложит оператор присваивания `<-`.
- Введите `>`, затем нажмите клавишу TAB, после чего RTVS предложит оператор конвейера `%>%`.

Фрагменты кода могут быть намного большим, чем просто завершение символов. Например, они могут освободить вас от необходимости запоминать имена параметров при вызове сложных функций, такие как этот фрагмент кода для считывания файла CSV с помощью функции `read.csv`.

![Анимации использования фрагмента кода для вставки вызова read.csv](media/code-snippet-expansion.gif)

В этом случае при вводе `readc` IntelliSense отображает список завершения. При выборе этого варианта в раскрывающемся списке и нажатии клавиши TAB выбирается вариант `readc`, а при повторном нажатии клавиши TAB фрагмента кода снова расширяется. (По этой причине расширение фрагмента кода зачастую рассматривается как "ввод фрагмента кода и двойное нажатие клавиши TAB".) В большинстве случаев при первом нажатии клавиши TAB завершается выбор варианта, предложенного IntelliSense, а при втором нажатии TAB запускается развертывание.

Чтобы просмотреть все доступные фрагменты кода, выберите **Сервис > Диспетчер фрагментов кода** (или нажмите клавиши CTRL + K, B) и выберите **R** для параметра **Язык**. Разверните группы и выберите отдельные фрагменты кода, чтобы ознакомиться с описанием и ярлыком.

![Диалоговое окно "Диспетчер фрагментов кода" для R](media/code-snippet-dialog.png)

Сведения о создании настраиваемых фрагментов кода см. в разделе [Пошаговое руководство. Создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md). В конечном счете фрагмент кода предоставляет собой лишь XML-файл. Например, ниже приведен фрагмент кода для оператора конвейера (ярлык `>`)

Обратите внимание, что фрагмент кода — это просто XML-файл. Ниже приведен фрагмент кода для оператора конвейера.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

XML-файлы для всех фрагментов кода устанавливаются вместе с RTVS; путь указан в поле **Расположение** в диалоговом окне **Диспетчер фрагментов кода**. Их также можно найти в исходном коде RTVS на сайте GitHub в разделе [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).

