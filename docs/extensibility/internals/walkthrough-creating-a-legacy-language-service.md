---
title: "Пошаговое руководство: Создание языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы [платформа управляемых пакетов], создание"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Пошаговое руководство: Создание языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

С помощью управляемых пакетов \(MPF\) языка классов framework для реализации службы языка в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] прост. Необходимо VSPackage для размещения службы языка, самой службы языка и средство синтаксического анализа для вашего языка.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## Расположения для шаблона Visual Studio Package  
 Шаблон проекта Visual Studio пакета можно найти в трех местах другой шаблон **Новый проект** диалоговое окно:  
  
1.  В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2.  В разделе Visual C\#, "Расширяемость". Язык проекта по умолчанию — C\#.  
  
3.  В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C\+\+.  
  
### Создать пакет VSPackage  
  
1.  Создайте новый пакет VSPackage с использованием шаблона проекта Visual Studio пакета.  
  
     При добавлении языковой службы существующий пакет VSPackage, пропустите следующие шаги и перейдите к процедуре «Создание класса службы языка».  
  
2.  Введите MyLanguagePackage в качестве имени проекта и нажмите кнопку **ОК**.  
  
     Можно использовать любое имя. Эти процедуры, описанный здесь предполагается MyLanguagePackage имени.  
  
3.  Выберите [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] язык и параметр для создания нового файла ключа. Нажмите кнопку **Далее**.  
  
4.  Введите соответствующие сведения о компании и пакета. Нажмите кнопку **Далее**.  
  
5.  Выберите **команды меню**. Нажмите кнопку **Далее**.  
  
     Если вы не собираетесь поддерживать фрагменты кода, просто нажмите кнопку Готово и пропустить следующий шаг.  
  
6.  Введите **Вставить фрагмент** как **имя команды** и `cmdidInsertSnippet` для **ИД команды**. Нажмите кнопку **Готово**.  
  
     **Имя команды** и **идентификатор команды** может быть что угодно, это только примеры.  
  
### Создание класса службы языка  
  
1.  В **обозревателе решений**, правой кнопкой мыши проект MyLanguagePackage, выберите пункт **Добавить**, **ссылки**, и нажмите кнопку **Добавить новую ссылку** кнопки.  
  
2.  В **Добавить ссылку** диалоговом **Microsoft.VisualStudio.Package.LanguageService** в **.NET** и нажмите кнопку **ОК**.  
  
     Это необходимо сделать только один раз для проекта языковой пакет.  
  
3.  В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **Добавить**, **класса**.  
  
4.  Убедитесь, что **класса** выбран в списке шаблонов.  
  
5.  Введите **MyLanguageService.cs** имя файла класса и нажмите кнопку **Добавить**.  
  
     Можно использовать любое имя. Ниже приведен в процедурах предполагается `MyLanguageService` имени.  
  
6.  Добавьте следующий код в файле MyLanguageService.cs `using` инструкции.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Изменить `MyLanguageService` являются производными от класса <xref:Microsoft.VisualStudio.Package.LanguageService> класса:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Поместите курсор на «LanguageService» и из **Изменить**, **IntelliSense** выберите пункт **реализовать абстрактный класс**. Это добавляет минимальные необходимые методы для реализации класса службы языка.  
  
9. Реализовать абстрактные методы, как описано в [Реализация службы языка](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### Регистрация службы языка  
  
1.  Откройте файл MyLanguagePackagePackage.cs и добавьте следующие `using` инструкции:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Зарегистрировать класс службы языка, как описано в [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md). Это включает в себя атрибуты ProvideXX и разделы «Proffering служба языка». Используйте MyLanguageService, где в этом разделе используется TestLanguageService.  
  
### Средство синтаксического анализа и сканера  
  
1.  Внедрить средства синтаксического анализа и проверки для конкретного языка, как описано в [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Реализация синтаксического анализа и сканера целиком управляется программистом и выходит за рамки этой статьи.  
  
## Компоненты службы языка  
 Для реализации каждого компонента в языковую службу, обычно создать класс, производный от соответствующего класса MPF языковой службы, реализовывать все абстрактные методы, при необходимости и переопределить соответствующие методы. Создание или наследовать классы зависят от возможностей, которую планируется поддерживать. Эти функции подробно описываются в [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md). Следующая процедура представляет общий подход для создания класса, производного от класса MPF.  
  
#### Наследование от класса MPF  
  
1.  В **обозревателе решений**, правой кнопкой мыши проект VSPackage и выберите **Добавить**, **класса**.  
  
2.  Убедитесь, что **класса** выбран в списке шаблонов.  
  
     Введите подходящее имя для файла класса и нажмите кнопку **Добавить**.  
  
3.  Добавьте следующий код в новый файл класса `using` инструкции.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Измените класс для наследования от нужного класса MPF.  
  
5.  Добавьте конструктор класса, который имеет по крайней мере те же параметры, как конструктор базового класса и передать параметры конструктора в конструкторе базового класса.  
  
     Например, конструктор для класса, производным от <xref:Microsoft.VisualStudio.Package.Source> класса может выглядеть следующим образом:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  От **Изменить**, **IntelliSense** выберите пункт **реализовать абстрактный класс** Если базовый класс содержит абстрактные методы, которые должны быть реализованы.  
  
7.  В противном случае — поместите курсор внутри класса и ввод переопределяемого метода.  
  
     Например, введите `public override` для просмотра списка всех методов, которые могут быть переопределены в этом классе.  
  
## См. также  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)