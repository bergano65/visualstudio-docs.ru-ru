---
title: "Создание заглушек методов модульного тестирования с помощью команды &quot;Создание модульных тестов&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 0194688e9eec258e415a30a8915379affc5f89de
ms.contentlocale: ru-ru
ms.lasthandoff: 06/02/2017

---
# <a name="get-started-with-microsoft-intellitest"></a>Приступая к работе с Microsoft IntelliTest

* Если вы сталкиваетесь с IntelliTest впервые:
  * посмотрите [видео на Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest);
  * прочитайте этот [обзор в журнале MSDN](https://msdn.microsoft.com/magazine/dn904672.aspx);
  * ознакомьтесь с [документацией](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest).
* Задайте вопрос на сайте [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest).
* Прочитайте остальную часть этого справочного руководства.
* Распечатайте эту страницу в качестве краткого справочника.

<a name="important-attributes"></a>
## <a name="important-attributes"></a>Важные атрибуты

* [PexClass](attribute-glossary.md#pexclass) помечает тип, содержащий **PUT**.
* [PexMethod](attribute-glossary.md#pexmethod) помечает **PUT**.
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) помечает параметр, отличный от NULL. 

```
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) привязывает тестовый проект к проекту.
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) указывает сборку для инструментирования.

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>Важные статические вспомогательные классы

* [PexAssume](static-helper-classes.md#pexassume) вычисляет предположения (фильтрация ввода).
* [PexAssert](static-helper-classes.md#pexassert) вычисляет утверждения.
* [PexChoose](static-helper-classes.md#pexchoose) создает новые варианты (дополнительные входные данные).
* [PexObserve](static-helper-classes.md#pexobserve) регистрирует динамические значения для созданных тестов.

```
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Хотите оставить отзыв?

Публикуйте свои идеи и запросы функций на сайте **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

