---
title: Практическое руководство. Изменение пространства имен доменного языка
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a237664a30dacf351edc048c82d8c9cdc304aa45
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775894"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Практическое руководство. Изменение пространства имен доменного языка
Вы можете изменить пространство имен доменного языка. Необходимо внести изменения в **обозреватель DSL**в свойствах проекта Dsl и в сведениях о сборке.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Чтобы изменить пространство имен доменного языка

1.  В **обозреватель DSL**, нажмите кнопку **Dsl** узла.

2.  В **свойства** измените **пространства имен** свойство.

3.  Сохраните решение и преобразования шаблонов.

4.  На **проекта** меню, щелкните **Dsl свойства**.

     Отобразятся свойства проекта.

5.  Перейдите на вкладку **Приложение** .

6.  Изменение **пространство имен по умолчанию** свойство на новое имя пространства имен.

7.  Если требуется, чтобы изменить имя сборки, измените **свойство имени сборки.**

8.  Если вы изменили имя сборки, откройте DslPackage\Package.tt и обновите следующую строку:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Если вы написали ни строчки кода, не забудьте заменить ссылки на пространство имен и класс в файлах кода.

10. Сброс Visual Studio экспериментального экземпляра.

    1.  Удалить **\Users\\**_{имя}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  В Windows **запустить** меню, выберите **все программы**, **Microsoft Visual Studio 2010 SDK**, **средства**, **сброса Экспериментальный экземпляр**.

11. На **построения** меню, выберите **Перестроить решение**.

## <a name="see-also"></a>См. также

- [Глоссарий по средствам доменного языка работы](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)