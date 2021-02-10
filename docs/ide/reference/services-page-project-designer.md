---
title: Страница "Службы" в конструкторе проектов
description: Сведения о том, как использовать страницу "Службы" конструктора проектов, чтобы включать и настраивать службы клиентских приложений для своего проекта.
ms.custom: SEO-VS-2020
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d9e564b6637feb19ef99c3d33c0ea5c1b7b1fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957833"
---
# <a name="services-page-project-designer"></a>Страница "Службы" в конструкторе проектов

Службы клиентских приложений предоставляют упрощенный доступ к службам входа, ролей и профилей [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] из приложений Windows Forms и Windows Presentation Foundation (WPF). Вы можете использовать страницу **Службы****конструктора проектов**, чтобы включать и настраивать службы клиентских приложений для своего проекта.

Благодаря службам клиентских приложений можно использовать централизованный сервер для проверки подлинности пользователей, определения ролей, назначенных каждому из пользователей, а также хранения индивидуальных параметров приложений, которые можно совместно использовать в рамках всей сети. Дополнительные сведения см. в разделе [Службы клиентских приложений](/dotnet/framework/common-client-technologies/client-application-services).

Чтобы открыть страницу **Службы**, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. Когда откроется окно **Конструктор проектов**, перейдите на вкладку **Службы**.

## <a name="task-list"></a>Список задач

[Практическое руководство. Настройка служб клиентских приложений](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса

 **Конфигурация**

Этот элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в разделе [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) или [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Платформа**

Этот элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в разделе [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) или [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Включить службы клиентских приложений**

Выберите, чтобы включить службы клиентских приложений. Требуется указать расположения служб на странице **Службы**, чтобы использовать службы клиентских приложений.

 **Использовать проверку подлинности Windows**

Указывает, что поставщик проверки подлинности будет использовать проверку подлинности Windows, то есть удостоверение, предоставленное операционной системой Windows.

 **Использовать проверку подлинности с помощью форм**

Указывает, что поставщик проверки подлинности будет использовать проверку подлинности с помощью форм. Это означает, что приложение должно предоставить пользовательский интерфейс для входа. Дополнительные сведения см. в разделе [Практическое руководство. Реализация входа пользователя с помощью служб клиентских приложений](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Местонахождение службы аутентификации**

Используется только для проверки подлинности на основе форм. Задает расположение службы проверки подлинности.

 **Дополнительно. Поставщик учетных данных**

Используется только для проверки подлинности на основе форм. Указывает реализацию <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>, которую служба аутентификации будет использовать для вывода диалогового окна входа в систему, если приложение вызывает метод `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> и передает пустые строки или `null` в качестве параметров. Если оставить это поле пустым, необходимо передать допустимое имя пользователя и пароль в метод <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Поставщиков учетных данных следует задать как имя типа с указанием сборки. Дополнительные сведения см. в разделах <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> и [Имена сборок](/dotnet/framework/app-domains/assembly-names). В простейшем виде имя типа сборки выглядит примерно так: `MyNamespace.MyLoginClass, MyAssembly`

 **Местонахождение службы ролей**

Указывает расположение службы ролей.

 **Местонахождение службы веб-параметров**

Указывает расположение службы профилей (веб-параметры).

 **Дополнительно**

Открывает диалоговое окно [Дополнительные параметры служб](../../ide/reference/advanced-settings-for-services-dialog-box.md), с помощью которого можно переопределить поведение по умолчанию. Например, с его помощью можно задать базу данных для автономного хранилища вместо использования локальной файловой системы. Дополнительные сведения см. в разделе [Расширенные параметры для диалогового окна служб](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>См. также раздел

- [Службы клиентских приложений](/dotnet/framework/common-client-technologies/client-application-services)
- [Диалоговое окно "Дополнительные параметры служб"](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Практическое руководство. Настройка служб клиентских приложений](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md)
