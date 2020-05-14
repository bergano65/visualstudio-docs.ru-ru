---
title: Создание страниц опций (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709151"
---
# <a name="create-options-pages"></a>Создание страниц опций
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] рамках управляемого пакета классы, полученные <xref:Microsoft.VisualStudio.Shell.DialogPage> из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, расширяют IDE, добавляя **страницы Options** в меню **Инструментов.**

 Объект, реализующий данную страницу **опции «Инструменты»,** связан с конкретными VSPackages по объекту. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>

 Поскольку среда мгновенно выполняет объект, реализующий определенную страницу **Параметры инструментов,** когда эта конкретная страница отображается IDE:

- Страница **Опции «Инструменты»** должна быть реализована на своем объекте, а не на объекте, реализуемом VSPackage.

- Объект не может реализовать несколько страниц **параметры инструментов.**

## <a name="register-as-a-tools-options-page-provider"></a>Зарегистрируйтесь в качестве поставщика страницы «Параметры инструментов»
 VSPackage, поддерживающий конфигурацию пользователя через страницы **Tools Options,** указывает <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> объекты, <xref:Microsoft.VisualStudio.Shell.Package> предоставляющие эти **страницы Параметры Инструментов,** применяя экземпляры, применяемые к реализации.

 Для каждого типа, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> полученного из полученных, <xref:Microsoft.VisualStudio.Shell.DialogPage>должен быть один экземпляр, который реализует страницу **Параметры инструментов.**

 Каждый <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> экземпляр использует тип, который реализует страницу **Параметры инструментов,** строки, содержащие категорию и подкатегорию, используемые для идентификации **страницы Параметры инструментов,** и информацию о ресурсах для регистрации типа как предоставляющего страницу **Параметры Инструментов.**

## <a name="persist-tools-options-page-state"></a>Состояние параметры «Устойчивые инструменты»
 Если реализация **страницы «Параметры инструментов»** зарегистрирована с включенной поддержкой автоматизации, IDE сохраняет состояние страницы вместе со всеми другими страницами **«Параметры инструментов».**

 VSPackage может управлять своей собственной <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>настойчивостью с помощью . Следует использовать только тот или иной метод настойчивости.

## <a name="implement-dialogpage-class"></a>Реализация класса DialogPage
 Объект, обеспечивающий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>типа -производные, может воспользоваться следующими унаследованные функциями:

- Окно пользовательского интерфейса по умолчанию.

- Механизм сохранения по умолчанию доступен либо в том случае, если <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> применяется к классу, либо если <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> свойство настроено `true` для того, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> что применяется к классу.

- Поддержка автоматизации.

  Минимальным требованием для объекта, реализующего <xref:Microsoft.VisualStudio.Shell.DialogPage> страницу **«Параметры инструментов»,** является добавление общедоступных свойств.

  Если класс правильно зарегистрирован в качестве поставщика **страницы Опционы Инструментов,** то его публичные свойства доступны в разделе **Параметры** меню **Инструментов** в виде сетки свойств.

  Все эти функции по умолчанию могут быть переопределены. Например, для создания более сложного пользовательского интерфейса <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>требуется только переопределение реализации по умолчанию.

## <a name="example"></a>Пример
 Ниже приводится простой "Привет мир" реализации страницы вариантов. Добавление следующего кода в проект по умолчанию, созданный шаблоном пакета Visual Studio с выбранным вариантом **Menu Command,** адекватно продемонстрирует функциональность страницы опции.

### <a name="description"></a>Описание
 Следующий класс определяет минимальную страницу опций "Hello world". При открытии пользователь может `HelloWorld` установить общественное имущество в сетке свойств.

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Описание
 Применение следующего атрибута к классу пакетов делает страницу опций доступной при загрузке пакета. Цифры являются произвольными идентификаторами ресурсов для категории и страницы, а значение Boolean в конце определяет, поддерживает ли страница автоматизацию.

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Описание
 Следующий обработчик событий отображает результат в зависимости от значения свойства, установленного на странице опционов. Он использует <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> метод с результатом явно бросили в пользовательский тип страницы опциона для доступа к свойствам, выставленным на странице.

 В случае проекта, генерируемого шаблоном пакета, `MenuItemCallback` позвоните в эту функцию из функции, чтобы прикрепить ее к команде по умолчанию, добавленной в меню **«Инструменты».**

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>См. также
- [Расширение настроек и параметров пользователя](../../extensibility/extending-user-settings-and-options.md)
- [Поддержка автоматизации страниц опционов](../../extensibility/internals/automation-support-for-options-pages.md)
