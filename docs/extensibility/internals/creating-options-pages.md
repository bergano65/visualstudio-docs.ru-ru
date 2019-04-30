---
title: Создание страниц "Параметры" | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d87e4002bd920a3b189886ae29bc7cf3a6ccf61f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910713"
---
# <a name="create-options-pages"></a>Создание страниц параметров
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформа managed package framework, классы, производные от <xref:Microsoft.VisualStudio.Shell.DialogPage> расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, добавив **параметры** страницы в разделе **средства** меню.

 Объект, реализующий заданный **Сервис, параметры** страница связана с определенной пакеты VSPackage, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> объекта.

 Поскольку среды создает экземпляр объекта, реализующего определенный **Сервис-Параметры** странице при отображении соответствующих страниц с помощью IDE:

- Объект **Сервис, параметры** страницы должен быть реализован на свой собственный объект, а не на объект, реализующий VSPackage.

- Объект не может реализовывать несколько **Сервис-Параметры** страниц.

## <a name="register-as-a-tools-options-page-provider"></a>Регистрируется как поставщик страницы параметров средств
 Конфигурацию VSPackage вспомогательные пользователя через **Сервис-Параметры** страниц показывает объекты, дает **Сервис-Параметры** страниц, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> применяется к <xref:Microsoft.VisualStudio.Shell.Package>реализации.

 Должен быть один экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для каждого <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип, реализующий **Сервис-Параметры** страницы.

 Каждый экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> использует тип, реализующий **Сервис-Параметры** страниц, строк, содержащих категорию и подкатегорию, используемый для идентификации **Сервис-Параметры** страницы, а также ресурсов сведения для регистрации типа как предоставляющего **Сервис-Параметры** страницы.

## <a name="persist-tools-options-page-state"></a>Сохранить состояние страницы параметров средств
 Если **Сервис-Параметры** реализация страницы зарегистрирован с поддержкой автоматизации, интегрированной среды разработки сохраняется состояние страницы, а также все остальные **Сервис-Параметры** страниц.

 VSPackage может управлять его собственной сохраняемости с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Следует использовать только один или другой метод сохраняемости.

## <a name="implement-dialogpage-class"></a>Реализация класса DialogPage
 Объект, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип может воспользоваться преимуществами следующих наследуемыми возможностями:

- Окно пользовательского интерфейса по умолчанию.

- Объект по умолчанию механизм сохраняемости, который доступен, либо если <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> применяется к классу, или если <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> свойству `true` для <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , применяемый к классу.

- Поддержка модели автоматизации.

  Минимальным требованием для объекта, реализующего **Сервис-Параметры** странице с помощью <xref:Microsoft.VisualStudio.Shell.DialogPage> заключается в добавлении общедоступного свойства.

  Если класс правильно зарегистрирован как **Сервис-Параметры** странице поставщика, а затем его общие свойства доступны на **параметры** раздел **средства** меню в форме сетки свойств.

  Все эти функции по умолчанию можно переопределить. Например, для создания более сложных пользователя интерфейс требует только переопределение реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.

## <a name="example"></a>Пример
 Ниже приведен реализацию простых «Hello world» страницы параметров. Добавив следующий код в проект по умолчанию создан с помощью шаблона пакета Visual Studio с **команды меню** выбран параметр будет адекватно продемонстрировать функциональные возможности параметра страницы.

### <a name="description"></a>Описание
 Следующий класс определяет страницу Параметры минимальной «Hello world». При открытии, пользователь может задать открытый `HelloWorld` свойства в сетке свойств.

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Описание
 Применение следующий атрибут к классу пакета доступны параметры, на странице при загрузке пакета. Числа являются произвольные идентификаторы ресурсов для категории и страницы, и логическое значение в конце указывает, поддерживает ли страница службы автоматизации.

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Описание
 Следующий обработчик событий возвращает результат в зависимости от значения свойства, заданного на странице параметров. Она использует <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> метод с результатом явным образом привести к типу страницы настраиваемый параметр для доступа к свойствам на странице.

 В случае проектов, созданных с помощью шаблона пакета, вызовите эту функцию из `MenuItemCallback` добавлена функция, чтобы присоединить его к команды по умолчанию для **средства** меню.

### <a name="code"></a>Код
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>См. также
- [Расширить пользовательские настройки и параметры](../../extensibility/extending-user-settings-and-options.md)
- [Поддержка автоматизации для страницы параметров](../../extensibility/internals/automation-support-for-options-pages.md)