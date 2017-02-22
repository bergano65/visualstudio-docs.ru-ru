---
title: "Создание кода из доменного языка | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Создание кода из доменного языка
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] предоставляет эффективный способ создания кода, документы, файлы конфигурации и другие артефакты из данных, представленных в моделях.  Использование [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]можно создать набор классов, представляющих данные, и можно написать свои текстовые шаблоны в классах, свойства которых имена и отражают данные.  
  
 Например, Fabrikam имеет XML\-файл имен и адресов электронной почты клиента.  Их разработчики создают модель, в которой клиент класс с именем свойства и электронной почте.  Они создают несколько текстовых шаблонов для обработки данных, включая этот фрагмент, который создает таблицу всех клиентов как часть html\-страницы.  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Если база данных клиента обрабатывается XML\-файл считывается в хранилище модели.  *Процессор директив*, созданный с помощью [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], делает доступным класса клиента к коду в текстовом шаблоне. Существует множество текстовых шаблонов не может быть запущен для одного и того же хранилища.  
  
 Текстовые шаблоны для [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  Они используются для создания исходного кода для элементов модели домена, так же как для VSPackage и элементов управления, используются для интеграции средств с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 В этом разделе обсуждаются некоторые способы создания, изменения и отладка текстовых шаблонов, используемые в [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## В этом подразделе  
 [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md)  
  
 Предоставляет основные сведения о обратившись к языку доменному в текстовых шаблонах.  
  
 [Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 Описывает, как сделать troubleshooting и отладку в текстовом шаблоне, который ссылается на доменному языку.  
  
 [Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Описывает, как подключить пользовательское основное приложение к созданному процессором директив.  
  
 [Команда DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Описывает командный файл, который выполняет исполняемый файл TextTransform из командной строки для текстовых шаблонов, которые ссылаются на доменных языков.  
  
## Ссылка  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директив текстового шаблона и управляющие блоки.  
  
## Связанные подразделы  
 [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Объясняет процесс преобразования текстового шаблона.  
  
 [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md)  
  
 Чтение этого раздела если создаются файлы из DSL на сервере построения.