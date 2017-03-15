---
title: "Создание страницы параметров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>Создание страницы параметров
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] платформа управляемых пакетов классы, производные от <xref:Microsoft.VisualStudio.Shell.DialogPage>расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, добавив **параметры** страниц в разделе **средства** меню.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Объект, реализующий данный **параметр средства** страница связана с конкретной VSPackages, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>объект.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Поскольку среда создает объект, реализующий определенный **Сервис Параметры** страницы при отображении соответствующих страниц в интегрированной среде разработки:  
  
-   Объект **параметр средства** страницы должен быть реализован на собственный объект, а не на объект, реализующий VSPackage.  
  
-   Объект не может реализовывать несколько **Сервис Параметры** страниц.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Регистрация в качестве поставщика средства параметры страницы  
 VSPackage вспомогательные пользовательскую конфигурацию через **Сервис Параметры** страниц показывает объекты, обеспечивая их **Сервис Параметры** страниц, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>применен к <xref:Microsoft.VisualStudio.Shell.Package>реализацию.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Должен быть один экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>для каждого <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип, реализующий **Сервис Параметры** страницы.</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Каждый экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>использует тип, реализующий **Сервис Параметры** страницы, строки, которые содержат категорию и подкатегорию, используемый для идентификации **Сервис Параметры** страницы, а также сведения о ресурсах для регистрации типа как **Сервис Параметры** страницы.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>Сохранение состояния страницы параметров инструментов  
 Если **Сервис Параметры** реализацию страницы зарегистрирован с поддержкой автоматизации, IDE сохраняет состояние страницы, а также все остальные **Сервис Параметры** страниц.  
  
 VSPackage можно управлять его собственной сохраняемости с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Следует использовать только одну или другим методом сохраняемости.  
  
## <a name="implementing-dialogpage-class"></a>Реализация класса DialogPage  
 Объект, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип можно воспользоваться преимуществами унаследованным следующие возможности:</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   Окно пользовательского интерфейса по умолчанию.  
  
-   Значение по умолчанию механизм сохранения доступны либо если <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>применяется к классу, или если <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>свойству `true` , <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>который применяется к классу</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   Поддержка модели автоматизации.  
  
 Минимальные требования для объекта, реализующего **Сервис Параметры** страницу с использованием <xref:Microsoft.VisualStudio.Shell.DialogPage>заключается в добавлении открытых свойств.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Если класс правильно зарегистрирован как **Сервис Параметры** страницы поставщика, а затем его общие свойства доступны на **параметры** раздел **средства** меню в виде сетки свойств.  
  
 Все эти функции по умолчанию можно переопределить. Например для создания более сложных пользовательского интерфейса требуется только переопределение реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>  
  
## <a name="example"></a>Пример  
 Ниже приведен простой реализации «hello world» страницы «параметры». Добавив следующий код в проект по умолчанию создан с помощью шаблона Visual Studio пакета с **команды меню** выбран параметр адекватно продемонстрирую функциональные возможности параметра страницы.  
  
### <a name="description"></a>Описание  
 Следующий класс определяет минимальной параметры страницы «hello world». При открытии, пользователь может задать открытый `HelloWorld` свойства в сетке свойств.  
  
### <a name="code"></a>Код  
 [!code-cs[#11 UI_UserSettings_ToolsOptionPages](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Описание  
 Применение в класс пакета следующий атрибут доступны параметры страницы при загрузке пакета. Числа являются произвольные идентификаторы ресурсов категории и страницы и логическое значение, в конце указывает, поддерживает ли страница автоматизации.  
  
### <a name="code"></a>Код  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Описание  
 Следующий обработчик событий отображает результат в зависимости от значения свойства, заданного на странице параметров. Он использует <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>метод с результатом явно привести к типу страницы настраиваемый параметр для доступа к свойствам на странице.</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 В случае с проектом, созданным с помощью шаблона пакета, вызвать эту функцию из `MenuItemCallback` добавлена функция, чтобы присоединить его к команды по умолчанию для **средства** меню.  
  
### <a name="code"></a>Код  
 [!code-cs[#08 UI_UserSettings_ToolsOptionPages](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>См. также  
 [Расширение настройки пользователя и параметры](../../extensibility/extending-user-settings-and-options.md)   
 [Поддержка модели автоматизации для страницы параметров](../../extensibility/internals/automation-support-for-options-pages.md)
