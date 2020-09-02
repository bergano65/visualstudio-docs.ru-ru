---
title: Создание кода на основе предметно-ориентированного языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666100"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Создание кода из доменного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Корпорация Майкрософт [!INCLUDE[dsl](../includes/dsl-md.md)] предоставляет мощный способ создания кода, документов, файлов конфигурации и других артефактов из данных, представленных в моделях. С помощью [!INCLUDE[dsl](../includes/dsl-md.md)] можно создать набор классов, представляющих ваши данные, а также создавать текстовые шаблоны в классах, имена и свойства которых отражают эти данные.

 Например, Fabrikam имеет XML-файл с именами клиентов и адресами электронной почты. Разработчики создают модель, в которой клиент является классом с именем и электронной почтой. Они пишут несколько текстовых шаблонов для обработки данных, включая этот фрагмент, который создает таблицу всех клиентов как часть HTML-страницы:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 При обработке базы данных клиента XML-файл считывается в хранилище моделей. *Обработчик директив*, созданный с помощью [!INCLUDE[dsl](../includes/dsl-md.md)] , делает класс Customer доступным для кода в текстовом шаблоне. Многие текстовые шаблоны можно запускать в одном хранилище.

 Текстовые шаблоны являются важными для [!INCLUDE[dsl](../includes/dsl-md.md)] . Они используются для создания исходного кода для элементов модели предметной области, а также для VSPackage и элементов управления, которые используются для интеграции инструментов с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 В этом разделе обсуждаются некоторые способы создания, изменения и отладки текстовых шаблонов, используемых в [!INCLUDE[dsl](../includes/dsl-md.md)] .

## <a name="in-this-section"></a>в этом разделе
 [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md)

 Содержит основные сведения о ссылках на доменный язык в текстовых шаблонах.

 [Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Описание процедуры устранения неполадок и отладки в текстовом шаблоне, который относится к доменному языку.

 [Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Описывает, как подключить пользовательский узел к созданному обработчику директив.

 [Команда DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Описание командного файла, выполняющего исполняемый файл TextTransform в командной строке для текстовых шаблонов, которые ссылаются на языки, относящиеся к домену.

## <a name="reference"></a>Справочник
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)

 Предоставляет синтаксис директив и управляющих блоков текстового шаблона.

## <a name="related-sections"></a>См. также
 [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Описывает процесс преобразования текстовых шаблонов.

 [Создание кода в процессе построения](../modeling/code-generation-in-a-build-process.md)

 Прочтите этот раздел, если вы создаете файлы с DSL на сервере сборки.
