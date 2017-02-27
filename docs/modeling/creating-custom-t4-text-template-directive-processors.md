---
title: "Creating Custom T4 Text Template Directive Processors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Creating Custom T4 Text Template Directive Processors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Процесс преобразования текстового шаблона* принимает файл *текстового шаблона* на входе и создает текстовый файл на выходе.  Для осуществления этого процесса *процессор преобразования текстового шаблона* управляет им и взаимодействует с узлом преобразования текстового шаблона и с одним или более *процессорами директив* текстового шаблона.  Дополнительные сведения см. в разделе [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Для создания пользовательского процессора директив создается класс, наследующий <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> либо <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Различие между этими двумя классами заключается в том, что <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> реализует минимальный интерфейс, необходимый для получения параметров от пользователя и генерирования кода, который создает выходной файл шаблона.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> реализует шаблон проектирования "требует\-предоставляет".  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> обрабатывает два специальных параметра, `requires` и `provides`.  Например, пользовательский процессор директив может принимать от пользователя имя файла, открывать и считывать этот файл, а затем сохранять содержащийся в нем текст в переменной с именем `fileText`.  Подкласс класса <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> может принимать от пользователя имя файла как значение параметра `requires` и имя переменной, в которой следует сохранить текст, как значение параметра `provides`.  Этот процессор откроет и прочитает файл, а затем сохранит его текст в заданной переменной.  
  
 Перед вызовом пользовательского процессора директив из текстового шаблона в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], его необходимо зарегистрировать.  
  
 Дополнительные сведения о том, как регистрируется ключ, см. в разделе [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).  
  
## Пользовательские директивы  
 Пользовательская директива выглядит так:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 Когда требуется осуществить доступ ко внешним данным или ресурсам из текстового шаблона, можно использовать процессор пользовательских директив.  
  
 Разные текстовые шаблоны могут совместно использовать функциональные возможности, предоставляемые одним процессором директив, поэтому процессоры директив предоставляют возможность создания кода для повторного использования.  Встроенная директива `include` является аналогичным средством, поскольку позволяет выносить код из файла и совместно использовать его в разных текстовых шаблонах.  Отличие заключается в том, что функциональные возможности директивы `include` фиксированы и она не принимает параметров.  Если требуется предоставить для текстовых шаблонов некоторые общие функциональные возможности, позволяющие шаблонам передавать параметры, то тогда следует создать пользовательский процессор директив.  
  
 Ниже приведено несколько примеров пользовательских процессоров директив.  
  
-   Процессор директив, который возвращает данные из базы данных и принимает имя пользователя и пароль в качестве параметров.  
  
-   Процессор директив для открытия и считывания файла, принимающий имя файла в качестве параметра.  
  
### Обязательные части пользовательского процессора директив  
 Для создания пользовательского процессора директив необходимо создать класс, наследующий <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> либо <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Ниже указаны наиболее важные методы класса `DirectiveProcessor`, которые необходимо реализовать.  
  
-   `bool IsDirectiveSupported(string directiveName)` – должен возвращать значение `true`, если процессор директив может обрабатывать именованные директивы.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` – процессор шаблонов вызывает этот метод для каждого вхождения директивы в шаблоне.  Ваш процессор должен сохранять результаты.  
  
 После всех вызовов ProcessDirective\(\) процессор шаблоном будет вызывать следующие методы.  
  
-   `string[] GetReferencesForProcessingRun()` – должен возвращать имена сборок, необходимых коду шаблона.  
  
-   `string[] GetImportsForProcessingRun()` – должен возвращать пространства имен, которые могут использоваться в коде шаблона.  
  
-   `string GetClassCodeForProcessingRun()` – должен возвращать код методов, свойств и другие определения, которые может использовать код шаблона.  Простейшим способом выполнения этих задач является построение строки, содержащей код на языке C\# или Visual Basic.  Чтобы процессор директив можно было вызывать из шаблона, использующего языки среды CLR, можно составлять операторы в виде дерева CodeDom и затем возвращать результат сериализации этого дерева на языке, используемом этим шаблоном.  
  
-   Дополнительные сведения см. в разделе [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## Содержание  
 [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md)  
 Поясняется, как зарегистрировать пользовательский процессор директив.  
  
 [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Описывается, как создать пользовательский процессор директив, зарегистрировать его и протестировать и как отформатировать выходной файл в виде HTML.