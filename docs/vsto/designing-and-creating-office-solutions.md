---
title: Разработка и создание решений Office
description: Узнайте, как Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания нескольких различных типов решений Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897633"
---
# <a name="design-and-create-office-solutions"></a>Разработка и создание решений Office

Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания решений Office различного типа. В этом разделе описываются шаблоны проектов и приведены рекомендации по созданию проектов Office. Сведения о том, как реализовать код и настройки пользовательского интерфейса после создания проекта, см. в разделе [Разработка решений Office](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Создание проектов Office
 Прежде чем начать, необходимо установить требования и определить наиболее оптимальный тип решения. Например, если решение Office должно запускаться при каждом использовании приложения, вашим требованиям лучше всего будут подходить надстройки VSTO. Если код тесно интегрирован с одиночным документом, создайте настройку на уровне документа. Проекты таких типов доступны как шаблоны проектов Visual Studio. Дополнительные сведения о шаблонах проектов Office, которые входят в состав Visual Studio, см. в статье [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md). Дополнительные сведения о создании проектов Office см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Проекты Office имеют возможности и элементы, отличные от проектов другого типа в Visual Studio. Например, при создании проекта на уровне документа документ или книгу в проекте можно открыть и изменить в Visual Studio. Дополнительные сведения см. [в статье проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Выберите версию платформа .NET Framework
 После выбора типа проекта, наилучшим образом подходящего вашим требованиям, можно выбрать версию платформы .NET Framework, которая будет использоваться в процессе разработки. В проектах Office можно применять следующие версии платформы .NET Framework:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  Для запуска решения на компьютерах конечных пользователей требуется выбранная версия платформа .NET Framework. Например, если проект предназначен для, на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] компьютерах конечных пользователей требуется. В этом примере решение не будет выполняться, если на компьютерах конечных пользователей установлено только платформа .NET Framework 3,5.

  При миграции проекта надстройки VSTO, который ориентирован на платформу .NET Framework 3.5, Visual Studio изменяет целевую платформу проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, в зависимости от установленной версии Office.

  Однако после того, как Visual Studio изменит целевую платформу, возможно, вам придется изменить некоторые части кода в проекте, если он использует определенные функции. Дополнительные сведения о том, как изменить целевую платформу, см. [в разделе инструкции. Назначение версии платформа .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Дополнительные сведения об изменениях, которые могут потребоваться в проекте, см. в статье [Перенос решений Office на платформа .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Если Visual Studio изменяет целевой платформа .NET Framework для проекта и вы используете ClickOnce для развертывания решения, убедитесь, что вы также выбрали соответствующую версию платформа .NET Framework в диалоговом окне **необходимые компоненты** . В случае изменения целевой платформы для своего проекта выбранное значение не будет изменяться автоматически. Дополнительные сведения см. в разделе [инструкции. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> В проектах Office, создаваемых с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], платформу .NET Framework 3.5 или более ранних версий использовать нельзя. Для проектов Office, создаваемых с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], требуются возможности, которые впервые появились в [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Сведения о том, когда требуются основные сборки взаимодействия Office на компьютерах конечных пользователей
 По умолчанию на компьютерах конечных пользователей не требуется устанавливать основные сборки взаимодействия Office, если свойству **Внедрить типы взаимодействия** каждой ссылки PIA Office в проекте присвоено значение **true**, которое является значением по умолчанию. В этом сценарии сведения о типе для типов PIA, используемых в решении, внедряются в сборку решения при сборке проекта. Во время выполнения внедренные сведения о типах используются вместо основных сборок взаимодействия для вызова основанной на COM объектной модели приложения Office. Дополнительные сведения о внедрении типов из основных сборок взаимодействия в решение см. в разделе [эквивалентность типов и внедренные типы взаимодействия](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Если свойству **Внедрить типы взаимодействия** для каждой ссылки PIA Office в проекте присвоено значение **false**, PIA Office должны быть установлены и зарегистрированы в глобальном кэше сборок на каждом компьютере конечного пользователя, на котором выполняется решение. В большинстве случаев эти сборки устанавливаются по умолчанию вместе с Office, но в свое решение вы также можете включить распространяемую сборку PIA как необходимый компонент. Дополнительные сведения см. в разделе [Предварительные требования для решения Office для развертывания](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Общие сведения о клиентском профиле
 Клиентский профиль .NET Framework — это подмножество полной платформы .NET Framework. Если необходимо использовать только клиентские возможности платформы .NET Framework и требуется обеспечить наиболее быстрый режим развертывания для решения Office, то можно использовать клиентский профиль .NET Framework. Дополнительные сведения см. в статье [платформа .NET Framework клиентский профиль](/dotnet/framework/deployment/client-profile).

 При создании проекта Office, ориентированного на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], по умолчанию используется [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]. Если вы хотите разработать полную версию [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , этот параметр необходимо установить после создания проекта. Дополнительные сведения см. в разделе [Практическое руководство. определить целевую версию .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Создание решений для 64-разрядного выпуска Microsoft Office
 Microsoft Office доступен в 64- и 32-разрядном выпусках. Для создания решений Office, которые могут выполняться в любом из выпусков, параметр платформы для проекта должен иметь значение **любой ЦП**. Это значение по умолчанию для проектов Office. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

 Существуют отдельные 64- и 32-разрядная версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которые используются в 64- и 32-разрядном выпусках Microsoft Office. Дополнительные сведения см. в статье [инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Сборки в решениях Office
 При создании проекта Office с помощью средств разработки решений на базе Office в Visual Studio разрабатываемый код в конечном итоге компилируется в сборку. Сборка развертывается на общем сервере или в каталоге на клиентском компьютере.

 Сборки в решениях Office загружаются приложением Office. После загрузки сборки код в сборке может отвечать на события, возникающие в приложении, например, если пользователь выбирает пункт меню. Код в сборке также может вызывать объектную модель для автоматизации и расширения приложения. Кроме того, он может использовать любой из классов в [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Дополнительные сведения см. в статье [Архитектура настроек уровня документа](../vsto/architecture-of-document-level-customizations.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).

 Для обозначения сборки решения Office используют манифесты развертывания и манифесты приложения. Манифесты содержат такие сведения как имя, версия и расположение сборки, чтобы приложение могло найти, установить связь со сборкой и запустить нужную сборку. Дополнительные сведения см. [в разделе Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Кроме сборки, проекты уровня документа содержат документ. Документ выступает в качестве внешнего интерфейса приложения и находится там, где происходит все взаимодействие с пользователем. С каждым документом может быть связана только одна основная сборка проекта. Однако на одну и ту же сборку могут указывать несколько документов.

 Сборки в проектах уровня документа не внедряются в документ. Они хранятся в другом месте и обозначаются манифестом приложения документа.

## <a name="security-considerations-for-assemblies"></a>Вопросы безопасности для сборок
 Чтобы решение Office могло работать на компьютере, сборки, используемые решением, должны иметь необходимый уровень доверия для выполнения. Дополнительные сведения о безопасности см. в статье [Защита решений Office](../vsto/securing-office-solutions.md).

 По умолчанию сборка решения и любые связанные сборки, которые находятся в выходной папке вашего проекта, имеют необходимый уровень доверия для запуска на компьютере разработчика при сборке проекта. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

 По соображениям безопасности проекты рекомендуется создавать на своем локальном компьютере, а не в общей папке. Дополнительные сведения см. в статье [Совместная разработка решений Office](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Связанные сборки
 Сборка может ссылаться на другие сборки, которые указаны в ссылках проекта. Однако одна сборка проекта уровня документа не может ссылаться на другую сборку проекта уровня документа.

## <a name="see-also"></a>См. также раздел
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Свойства в проектах Office](../vsto/properties-in-office-projects.md)
- [Запуск решений в разных версиях Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Пошаговое руководство. Назначение приложений Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Как настроить сведения о конфигурации для решения Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Использование функций Office в Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Распространенные задачи в программировании Office](../vsto/common-tasks-in-office-programming.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)