---
title: 'Пошаговое руководство: Создание службы языка для прежних версий | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb1fc7b6c35b2ee6ef3a767f7093f2fa0e4cb972
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144938"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Пошаговое руководство: Создание службы языка для прежних версий
С помощью языка классы managed package framework (MPF) для реализации службы языка в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] нетрудно. Требуется пакет VSPackage для размещения службы языка, самой службы языка и средство синтаксического анализа для конкретного языка.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения для шаблона Visual Studio Package  
 Шаблон проекта пакета Visual Studio можно найти в трех местах другой шаблон **новый проект** диалоговое окно:  
  
1.  В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2.  В разделе Visual C#, "Расширяемость". Язык проекта по умолчанию — C#.  
  
3.  В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C++.  
  
### <a name="create-a-vspackage"></a>Создать пакет VSPackage  
  
1.  Создайте новый пакет VSPackage с использованием шаблона проекта пакета Visual Studio.  
  
     Если языковой службы добавляются к существующей VSPackage, пропустите следующие шаги и перейдите к процедуре «Создание класса службы языка».  
  
2.  Введите имя проекта MyLanguagePackage и нажмите кнопку **ОК**.  
  
     Можно использовать любое имя по необходимости. Описанный здесь подразумевается MyLanguagePackage как имя.  
  
3.  Выберите [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] язык и возможность создать новый файл ключа. Нажмите кнопку **Далее**.  
  
4.  Введите соответствующие сведения о компании и пакета. Нажмите кнопку **Далее**.  
  
5.  Выберите **команду меню**. Нажмите кнопку **Далее**.  
  
     Если вы не собираетесь поддерживать фрагменты кода, просто нажмите кнопку Готово и пропустить следующий шаг.  
  
6.  Введите **вставить фрагмент** как **команды имя** и `cmdidInsertSnippet` для **ИД команды**. Нажмите кнопку **Готово**.  
  
     **Имя команды** и **идентификатор команды** можно указать любое, это только примеры.  
  
### <a name="create-the-language-service-class"></a>Создание класса службы языка  
  
1.  В **обозревателе решений**, правой кнопкой мыши проект MyLanguagePackage, выберите **добавить**, **ссылки**и нажмите кнопку **добавить новую ссылку** кнопки.  
  
2.  В **добавить ссылку** выберите **Microsoft.VisualStudio.Package.LanguageService** в **.NET** и нажмите кнопку **ОК**.  
  
     Это необходимо сделать только один раз для пакета проекта языка.  
  
3.  В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **добавить**, **класса**.  
  
4.  Убедитесь, что **класса** выбран в списке шаблонов.  
  
5.  Введите **MyLanguageService.cs** для имени файла класса, и нажмите кнопку **добавить**.  
  
     Можно использовать любое имя по необходимости. Описанный здесь подразумевается `MyLanguageService` как имя.  
  
6.  Добавьте следующие строки в файле MyLanguageService.cs `using` инструкции.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Изменить `MyLanguageService` являются производными от класса <xref:Microsoft.VisualStudio.Package.LanguageService> класса:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Поместите курсор на «LanguageService» и из **изменить**, **IntelliSense** последовательно выберите пункты **реализовать абстрактный класс**. Это добавляет минимальные необходимые методы для реализации класса службы языка.  
  
9. Реализуйте абстрактные методы, как описано в [реализации службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Регистрация службы языка  
  
1.  Откройте файл MyLanguagePackagePackage.cs и добавьте следующие `using` инструкции:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Зарегистрируйте класс службы языка, как описано в [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md). Это включает в себя атрибуты ProvideXX и разделы «Proffering служба языка». Используйте MyLanguageService, где в этом разделе используется TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>Средство синтаксического анализа и сканера  
  
1.  Реализуйте средство синтаксического анализа и сканер для конкретного языка, как описано в [средство синтаксического анализа службы языка для прежних версий и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Реализация синтаксического анализа и сканер разработчик и выходит за рамки этой статьи.  
  
## <a name="language-service-features"></a>Возможности службы языка  
 На реализацию каждой функции в службе языка, вы обычно создайте класс, производный от соответствующего класса службы языка MPF, реализовывать все абстрактные методы при необходимости и переопределить соответствующие методы. Классы можно создать и/или являются производными от зависят от возможностей планируется поддержка. Эти функции подробно описываются в [возможности службы языка для прежних версий](../../extensibility/internals/legacy-language-service-features1.md). Ниже описан общий подход для создания класса, производного от классов MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Наследование от класса MPF  
  
1.  В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **добавить**, **класса**.  
  
2.  Убедитесь, что **класса** выбран в списке шаблонов.  
  
     Введите подходящее имя для файла класса и нажмите кнопку **добавить**.  
  
3.  В новый файл класса, добавьте следующие `using` инструкции.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Измените класс для наследования от нужного класса MPF.  
  
5.  Добавьте конструктор класса, который имеет по крайней мере те же параметры, как конструктор базового класса и передайте параметры конструктора в конструкторе базового класса.  
  
     Например, конструктор для класса, производного от <xref:Microsoft.VisualStudio.Package.Source> класс может выглядеть следующим образом:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Из **изменить**, **IntelliSense** последовательно выберите пункты **реализовать абстрактный класс** Если базовый класс содержит абстрактные методы, которые должны быть реализованы.  
  
7.  В противном случае — поместите курсор внутри класса и ввод переопределяемого метода.  
  
     Например, введите `public override` для просмотра списка всех методов, которые могут быть изменены в этом классе.  
  
## <a name="see-also"></a>См. также  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)