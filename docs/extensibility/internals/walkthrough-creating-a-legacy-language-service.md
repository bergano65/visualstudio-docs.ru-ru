---
title: 'Пошаговое: Создание службы наследование языка (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703691"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Пошаговое руководство. Создание языковой службы прежних версий
Использование языковых классов управляемого пакета (MPF) [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] для реализации языковой службы в несложно. Вам нужен VSPackage для размещения языковой службы, самого языкового сервиса и парсера для вашего языка.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../../extensibility/visual-studio-sdk.md)

## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения шаблона проекта пакета Visual Studio
 Шаблон проекта Visual Studio Package можно найти в трех различных местах шаблона в диалоговом окне **нового проекта:**

1. В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.

2. В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.

3. В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.

### <a name="create-a-vspackage"></a>Создание VSPackage

1. Создайте новый VSPackage с шаблоном проекта Visual Studio Package.

    Если вы добавляете языковую службу в существующий VSPackage, пропустите следующие шаги и перейдите непосредственно к процедуре "Создать языковой сервис".

2. Введите MyLanguagePackage для названия проекта и нажмите **OK**.

    Вы можете использовать любое имя, которое вы хотите. Эти процедуры, описанные здесь, предполагают, что MyLanguagePackage является названием.

3. Выберите [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] в качестве языка и возможность создания нового файла ключа. Щелкните **Далее**.

4. Введите соответствующую информацию о компании и упаковке. Щелкните **Далее**.

5. Выберите **команду меню**. Щелкните **Далее**.

    Если вы не собираетесь поддерживать фрагменты кода, вы можете просто нажать finish и проигнорировать следующий шаг.

6. Введите **фрагмент вставки** `cmdidInsertSnippet` в качестве названия **командования** и для **идентификатора команды.** Нажмите кнопку **Готово**.

    **Название команды** и **идентификатор команды** могут быть любыми, что вы хотите, это всего лишь примеры.

### <a name="create-the-language-service-class"></a>Создание класса языковой службы

1. В **Solution Explorer**, правое нажатие на проект MyLanguagePackage, **выберите Добавить,** **Справка**, а затем выбрать кнопку **Добавить новую ссылку.**

2. В диалоговом окне **Добавления** выберите **Microsoft.VisualStudio.Package.LanguageService** в вкладке **.NET** и **нажмите OK**.

     Это необходимо сделать только один раз для проекта языкового пакета.

3. В **Solution Explorer**, правое нажатие на проект VSPackage и выберите **Добавить,** **Класс**.

4. Убедитесь, что **класс** выбран в списке шаблонов.

5. Введите **MyLanguageService.cs** для названия файла класса и нажмите **Добавить**.

     Вы можете использовать любое имя, которое вы хотите. Эти процедуры, `MyLanguageService` описанные здесь, предполагают название.

6. В файле MyLanguageService.cs добавьте следующие `using` директивы.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Измените `MyLanguageService` класс, чтобы <xref:Microsoft.VisualStudio.Package.LanguageService> извлечь из класса:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Расположите курсор на "LanguageService" и из меню **Edit**, **IntelliSense,** выберите **Реализация Абстрактный класс**. Это добавляет минимальные необходимые методы для реализации класса языковых служб.

9. Реализация абстрактных методов, описанных в [реализации службы языка Legacy.](../../extensibility/internals/implementing-a-legacy-language-service2.md)

### <a name="register-the-language-service"></a>Регистрация языковой службы

1. Откройте файл MyLanguagePackagePackage.cs и `using` добавьте следующие директивы:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Зарегистрируйте свой класс языкового обслуживания, как описано в [регистрации службы Legacy Language Service.](../../extensibility/internals/registering-a-legacy-language-service1.md) Это включает в себя атрибуты ProvideXX и разделы "Предложение языковой службы". Используйте MyLanguageService, где эта тема использует TestLanguageService.

### <a name="the-parser-and-scanner"></a>Парсер и сканер

1. Внедрить парсер и сканер для вашего языка, как описано в [Legacy Language Service Parser and Scanner.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

     То, как вы реализуете свой парсер и сканер, полностью зависит от вас и выходит за рамки этой темы.

## <a name="language-service-features"></a>Особенности языковой службы
 Для реализации каждой функции в языковой службе обычно вычеркаете класс из соответствующего класса языковой службы MPF, реализуете любые по мере необходимости абстрактные методы и перечеркаете соответствующие методы. Какие классы вы создаете и/или получаете, зависит от функций, которые вы собираетесь поддерживать. Эти функции подробно обсуждаются в [функциях Службы языка Legacy.](../../extensibility/internals/legacy-language-service-features1.md) Следующей процедурой является общий подход к вывозу класса из классов MPF.

#### <a name="deriving-from-an-mpf-class"></a>Выдергивание из класса MPF

1. В **Solution Explorer**, правое нажатие на проект VSPackage и выберите **Добавить,** **Класс**.

2. Убедитесь, что **класс** выбран в списке шаблонов.

     Введите подходящее имя для файла класса и нажмите **Добавить**.

3. В новом файле класса `using` добавьте следующие директивы.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Измените класс, чтобы извлечь из желаемого класса MPF.

5. Добавьте конструктор класса, который принимает по крайней мере те же параметры, что и конструктор базового класса, и передайте параметры конструктора базового класса на конструктор базового класса.

     Например, конструктор для класса, полученный <xref:Microsoft.VisualStudio.Package.Source> из класса, может выглядеть следующим образом:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Из меню **Edit**, **IntelliSense** выберите **«Реализация абстрактного класса»,** если базовый класс имеет какие-либо абстрактные методы, которые должны быть реализованы.

7. В противном случае, положение caret внутри класса и введите метод, который будет переопределен.

     Например, `public override` введите список всех методов, которые могут быть переопределены в этом классе.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
