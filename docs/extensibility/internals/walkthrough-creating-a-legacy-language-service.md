---
title: Пошаговое руководство. Создание языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d58234dbe503f8d086e081464c2e38f759a75e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907925"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Пошаговое руководство. Создание языковой службы прежних версий
С помощью управляемых пакетов (MPF) языка классов framework для реализации службы языка в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] прост. Вам потребуется VSPackage для размещения службы языка, сама служба языка и средство синтаксического анализа для вашего языка.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения для шаблона Visual Studio Package
 Шаблон проекта пакета Visual Studio можно найти в трех местах другой шаблон **новый проект** диалоговое окно:

1. В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.

2. В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.

3. В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.

### <a name="create-a-vspackage"></a>Создание пакета VSPackage

1. Создание нового пакета VSPackage с помощью шаблона проекта пакета Visual Studio.

    При добавлении языковой службы для существующего пакета VSPackage, пропустите следующие шаги и перейдите к процедуре «Создание класса службы языка».

2. Введите MyLanguagePackage для имени проекта и нажмите кнопку **ОК**.

    Можно использовать любое имя, которое будет. Эти процедуры, описанные здесь предполагается MyLanguagePackage как имя.

3. Выберите [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] язык и возможность создать новый файл ключа. Нажмите кнопку **Далее**.

4. Введите соответствующие сведения о компании и пакета. Нажмите кнопку **Далее**.

5. Выберите **команды меню**. Нажмите кнопку **Далее**.

    Если вы не собираетесь поддерживать фрагменты кода, можно просто щелкните "Готово" и пропустить следующий шаг.

6. Введите **вставить фрагмент** как **имя команды** и `cmdidInsertSnippet` для **ИД команды**. Нажмите кнопку **Готово**.

    **Имя команды** и **идентификатор команды** может быть любым, но это только примеры.

### <a name="create-the-language-service-class"></a>Создание класса службы языка

1. В **обозревателе решений**MyLanguagePackage проект правой кнопкой мыши, выберите пункт **добавить**, **ссылку**, а затем выберите **добавить новую ссылку** кнопки.

2. В **добавить ссылку** выберите **Microsoft.VisualStudio.Package.LanguageService** в **.NET** вкладку и нажмите кнопку **ОК**.

     Это необходимо сделать только один раз для языка проекта.

3. В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **добавить**, **класс**.

4. Убедитесь, что **класс** выбран в списке шаблонов.

5. Введите **MyLanguageService.cs** в качестве имени в файл класса и нажмите кнопку **добавить**.

     Можно использовать любое имя, которое будет. Эти процедуры, описанные здесь предполагается `MyLanguageService` как имя.

6. В файле MyLanguageService.cs, добавьте следующий `using` инструкций.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Изменить `MyLanguageService` класса для наследования от <xref:Microsoft.VisualStudio.Package.LanguageService> класса:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Поместите курсор на «LanguageService», а **изменить**, **IntelliSense** меню, выберите **реализовать абстрактный класс**. Это добавляет минимальные необходимые методы для реализации класса службы языка.

9. Реализовать абстрактные методы, как описано в разделе [реализации языковой службы прежних](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Регистрация языковой службы

1. Откройте файл MyLanguagePackagePackage.cs и добавьте следующий `using` инструкции:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Регистрация класса службы языка, как описано в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md). Сюда входят атрибуты ProvideXX и разделы «Proffering служба языка». Используйте MyLanguageService, где в этом разделе используется TestLanguageService.

### <a name="the-parser-and-scanner"></a>Средство синтаксического анализа и сканер

1. Реализуйте средство синтаксического анализа и сканер для используемого языка, как описано в [средства синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Как реализовать средство синтаксического анализа и сканер разработчик и выходит за рамки этой статьи.

## <a name="language-service-features"></a>Функции языковой службы
 Для реализации каждого компонента в службе языка, вы обычно создать класс, производный от соответствующего класса службы языка MPF, реализовать все абстрактные методы при необходимости и переопределить соответствующие методы. Классы можно создать и/или являются производными от зависят от возможностей, которую планируется поддерживать. Эти функции подробно описаны в [функции службы языка для прежних версий](../../extensibility/internals/legacy-language-service-features1.md). Ниже описан общий подход к наследование класса от классы MPF.

#### <a name="deriving-from-an-mpf-class"></a>Наследование от класса MPF

1. В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **добавить**, **класс**.

2. Убедитесь, что **класс** выбран в списке шаблонов.

     Введите подходящее имя для файла класса и нажмите кнопку **добавить**.

3. В новый файл класса, добавьте следующий `using` инструкций.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Измените класс для наследования от требуемого класса MPF.

5. Добавьте конструктор класса, который занимает не менее те же параметры, что конструктор базового класса и передайте параметры конструктора в конструкторе базового класса.

     Например, конструктор для класса, производного от <xref:Microsoft.VisualStudio.Package.Source> класс может выглядеть следующим образом:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Из **изменить**, **IntelliSense** меню, выберите **реализовать абстрактный класс** Если базовый класс содержит абстрактные методы, которые должны быть реализованы.

7. В противном случае поместите курсор внутри класса и укажите метод для переопределения.

     Например, введите `public override` для просмотра списка всех методов, которые могут быть переопределены в этом классе.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)