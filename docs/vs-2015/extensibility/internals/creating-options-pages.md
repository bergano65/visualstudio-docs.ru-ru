---
title: Создание страниц "Параметры" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106128"
---
# <a name="creating-options-pages"></a>Создание страниц параметров
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] платформа managed package framework, классы, производные от <xref:Microsoft.VisualStudio.Shell.DialogPage> расширить [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, добавив **параметры** страницы в разделе **средства** меню.  
  
 Объект, реализующий заданный **Сервис, параметры** страница связана с определенной пакеты VSPackage, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> объекта.  
  
 Поскольку среды создает экземпляр объекта, реализующего определенный **Сервис-Параметры** странице при отображении соответствующих страниц с помощью IDE:  
  
- Объект **Сервис, параметры** страницы должен быть реализован на свой собственный объект, а не на объект, реализующий VSPackage.  
  
- Объект не может реализовывать несколько **Сервис-Параметры** страниц.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Регистрация в качестве поставщика страницы параметров средств  
 Конфигурацию VSPackage вспомогательные пользователя через **Сервис-Параметры** страниц показывает объекты, дает **Сервис-Параметры** страниц, применяя экземпляров <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> применяется к <xref:Microsoft.VisualStudio.Shell.Package>реализации.  
  
 Должен быть один экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для каждого <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип, реализующий **Сервис-Параметры** страницы.  
  
 Каждый экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> использует тип, реализующий **Сервис-Параметры** страниц, строк, содержащих категорию и подкатегорию, используемый для идентификации **Сервис-Параметры** страницы, а также ресурсов сведения для регистрации типа как предоставляющего **Сервис-Параметры** страницы.  
  
## <a name="persisting-tools-options-page-state"></a>Сохранение состояния страниц параметров средств  
 Если **Сервис-Параметры** реализация страницы зарегистрирован с поддержкой автоматизации, интегрированной среды разработки сохраняется состояние страницы, а также все остальные **Сервис-Параметры** страниц.  
  
 VSPackage может управлять его собственной сохраняемости с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Следует использовать только один или другой метод сохраняемости.  
  
## <a name="implementing-dialogpage-class"></a>Реализация класса DialogPage  
 Объект, предоставляющий реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>-производный тип может воспользоваться преимуществами следующих наследуемыми возможностями:  
  
- Окно пользовательского интерфейса по умолчанию.  
  
- Объект по умолчанию механизм сохраняемости, который доступен, либо если <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> применяется к классу, или если <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> свойству `true` для <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , применяемый к классу.  
  
- Поддержка модели автоматизации.  
  
  Минимальным требованием для объекта, реализующего **Сервис-Параметры** странице с помощью <xref:Microsoft.VisualStudio.Shell.DialogPage> заключается в добавлении общедоступного свойства.  
  
  Если класс правильно зарегистрирован как **Сервис-Параметры** странице поставщика, а затем его общие свойства доступны на **параметры** раздел **средства** меню в форме сетки свойств.  
  
  Все эти функции по умолчанию можно переопределить. Например, для создания более сложных пользователя интерфейс требует только переопределение реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Пример  
 Ниже приведен простой реализации «hello world» страницы параметров. Добавив следующий код в проект по умолчанию создан с помощью шаблона пакета Visual Studio, с **команды меню** выбран параметр будет адекватно продемонстрировать функциональные возможности параметра страницы.  
  
### <a name="description"></a>Описание  
 Следующий класс определяет минимальной параметры страницы «hello world». При открытии, пользователь может задать открытый `HelloWorld` свойства в сетке свойств.  
  
### <a name="code"></a>Код  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Описание  
 Применение следующий атрибут к классу пакета доступны параметры, на странице при загрузке пакета. Числа являются произвольные идентификаторы ресурсов для категории и страницы, и логическое значение в конце указывает, поддерживает ли страница службы автоматизации.  
  
### <a name="code"></a>Код  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Описание  
 Следующий обработчик событий возвращает результат в зависимости от значения свойства, заданного на странице параметров. Она использует <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> метод с результатом явным образом привести к типу страницы настраиваемый параметр для доступа к свойствам на странице.  
  
 В случае проектов, созданных с помощью шаблона пакета, вызовите эту функцию из `MenuItemCallback` добавлена функция, чтобы присоединить его к команды по умолчанию для **средства** меню.  
  
### <a name="code"></a>Код  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>См. также  
 [Расширение пользовательские настройки и параметры](../../extensibility/extending-user-settings-and-options.md)   
 [Поддержка автоматизации страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)
