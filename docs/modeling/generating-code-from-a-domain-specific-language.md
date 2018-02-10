---
title: "Создание кода из доменного языка | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ad823ee772119f6398e47e6df6211360468b13ad
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="generating-code-from-a-domain-specific-language"></a>Создание кода из доменного языка
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] предоставляет эффективный способ создания кода, документов, файлов конфигурации и другие артефакты из данных, представленных в модели. С помощью [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], можно создать набор классов, представляющих данные и вы можете использовать текстовые шаблоны в классах, имена и свойства отражают данные.  
  
 Например компании Fabrikam имеет XML-файл имена заказчиков и адресов электронной почты. Разработчики создать модель, в которой клиент — это класс, с именем свойства и электронной почты. Они записывают несколько текстовых шаблонов для обработки данных, включая этот фрагмент, в которой создается таблица всех клиентов в рамках HTML-страницы:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 При обработке базы данных клиента в хранилище моделей считывается XML-файл. Объект *процессора директив*, созданный с помощью [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], делает классу "Customer" доступным для кода в текстовый шаблон. Для одного хранилища можно запустить несколько текстовых шаблонов.  
  
 Текстовые шаблоны, необходимы для [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Они используются для создания исходного кода для элементов модели домена также VSPackage и элементы управления, которые используются для интеграции средств с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 В этом разделе рассматриваются некоторые из этих способов создания, изменения и отладки текстовых шаблонов, используемых в [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обращение к моделям из текстовых шаблонов](../modeling/accessing-models-from-text-templates.md)  
  
 Основные сведения о ссылке на доменного языка в текстовых шаблонах.  
  
 [Пошаговое руководство. Отладка текстового шаблона, обращающегося к модели](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Описывает, как выполнить устранение неисправностей и отладка в текстовый шаблон, который ссылается на доменного языка.  
  
 [Пошаговое руководство. Связывание основного приложения с генерируемым обработчиком директив](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Описывает способ соединения пользовательского основного приложения, созданного процессора директив.  
  
 [Команда DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Описывает командный файл, который выполняет исполняемый объект TextTransform в командной строке для текстовых шаблонов, которые ссылаются на доменные языки.  
  
## <a name="reference"></a>Ссылка  
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директив текстового шаблона и управляющие блоки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Описывается процесс преобразования текстового шаблона.  
  
 [Создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md)  
  
 Прочитайте эту статью, при создании файлов из DSL на сервере сборки.