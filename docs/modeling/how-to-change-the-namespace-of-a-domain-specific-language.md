---
title: Как выполнить Изменение пространства имен доменного языка
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 3209f1942e95e8cfd883f938722ccfbc713e64db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890002"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Как выполнить Изменение пространства имен доменного языка

Вы можете изменить пространство имен доменного языка. Внесите изменения в **обозреватель DSL**в свойствах проекта Dsl и в сведениях о сборке.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Чтобы изменить пространство имен доменного языка

1. В **обозреватель DSL**выберите **Dsl** узла.

2. В **свойства** измените **пространства имен** свойство.

3. Сохраните решение и преобразования шаблонов.

4. На **проекта** меню, выберите **Dsl свойства**.

   Отобразятся свойства проекта.

5. Выберите **приложения** вкладки.

6. Изменение **пространство имен по умолчанию** свойство на новое имя пространства имен.

7. Если требуется, чтобы изменить имя сборки, измените **свойство имени сборки.**

8. Если вы изменили имя сборки, откройте DslPackage\Package.tt и обновите следующую строку:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Если вы написали ни строчки кода, не забудьте заменить ссылки на пространство имен и класс в файлах кода.

10. Сброс Visual Studio экспериментального экземпляра.

    1. Удалить **\Users\\**_{имя}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. В Windows **запустить** меню, выберите **все программы** > **Microsoft Visual Studio 2010 SDK** > **средства**  >  **Сброс экспериментального экземпляра**.

11. На **построения** меню, выберите **Перестроить решение**.

## <a name="see-also"></a>См. также

[Глоссарий по средствам доменного языка работы](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)