---
title: Проектирование и создание решений Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e43824ed3fa34a7cd22b98fb25f946f36cb8eab6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="designing-and-creating-office-solutions"></a>Designing and Creating Office Solutions
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания решений Office различного типа. В этом разделе описываются шаблоны проектов и приведены рекомендации по созданию проектов Office. Сведения о реализации кода и настроек пользовательского интерфейса после создания проекта см. в разделе [разработка решений Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="creating-office-projects"></a>Создание проектов Office  
 Прежде чем начать, необходимо установить требования и определить наиболее оптимальный тип решения. Например, если решение Office должно запускаться при каждом использовании приложения, вашим требованиям лучше всего будут подходить надстройки VSTO. Если код тесно интегрирован с одиночным документом, создайте настройку на уровне документа. Проекты таких типов доступны как шаблоны проектов Visual Studio. Дополнительные сведения о шаблонах проектов Office, которые входят в состав Visual Studio см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md). Дополнительные сведения о создании проектов Office см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Проекты Office имеют возможности и элементы, отличные от проектов другого типа в Visual Studio. Например, при создании проекта на уровне документа документ или книгу в проекте можно открыть и изменить в Visual Studio. Дополнительные сведения см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choosing-a-net-framework-version"></a>Выбор версии .NET Framework  
 После выбора типа проекта, наилучшим образом подходящего вашим требованиям, можно выбрать версию платформы .NET Framework, которая будет использоваться в процессе разработки. В проектах Office можно применять следующие версии платформы .NET Framework:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 Версия .NET Framework, которую вы выбрали для своего проекта, требуется на компьютерах конечных пользователей, где будет работать ваше решение. Например, если в вашем проекте применяется [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], на компьютерах конечных пользователей необходимо иметь [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этом примере решение не будет работать, если на компьютерах пользователей установлена только платформа .NET Framework 3.5.  
  
 При миграции проекта надстройки VSTO, который ориентирован на платформу .NET Framework 3.5, Visual Studio изменяет целевую платформу проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, в зависимости от установленной версии Office.  
  
 Однако после того, как Visual Studio изменит целевую платформу, возможно, вам придется изменить некоторые части кода в проекте, если он использует определенные возможности. Дополнительные сведения об изменении целевой версии .NET framework см. в разделе [как: целевой версии платформы .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Дополнительные сведения об изменениях, может потребоваться внести в проект см. в разделе [Migrating Office Solutions .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Если Visual Studio изменяет платформы .NET Framework для проекта и для развертывания решения используется ClickOnce, убедитесь, что также выбрать соответствующую версию платформы .NET Framework в **необходимые компоненты** диалоговое окно. В случае изменения целевой платформы для своего проекта выбранное значение не будет изменяться автоматически. Дополнительные сведения см. в разделе [как: Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  В проектах Office, создаваемых с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], платформу .NET Framework 3.5 или более ранних версий использовать нельзя. Для проектов Office, создаваемых с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], требуются функции, которые впервые появились в [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].  
  
### <a name="understanding-when-the-office-pias-are-required-on-end-user-computers"></a>Определение ситуаций, когда основные сборки взаимодействия Office требуются на компьютерах конечных пользователей  
 По умолчанию, основных сборок взаимодействия Office (PIA) не обязательно должны быть установлены на компьютерах конечных пользователей, если **внедрить типы взаимодействия** каждой ссылки на основную сборку ВЗАИМОДЕЙСТВИЯ Office в проекте свойству **True**, который значение по умолчанию. В этом сценарии сведения о типе для типов PIA, используемых в решении, внедряются в сборку решения при сборке проекта. Во время выполнения внедренные сведения о типах используются вместо основных сборок взаимодействия для вызова основанной на COM объектной моделью приложения Office. Дополнительные сведения о как внедренные типы из основных сборок взаимодействия в решение см. в разделе [эквивалентности типов и внедренных типов взаимодействия](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Если **внедрить типы взаимодействия** каждой ссылки на основную сборку ВЗАИМОДЕЙСТВИЯ Office в проекте свойству **False**, основных сборок взаимодействия Office необходимо установить и зарегистрировать в глобальном кэше сборок на каждом компьютере конечного пользователя, выполняется решение. В большинстве случаев эти сборки устанавливаются по умолчанию вместе с Office, но в свое решение вы также можете включить распространяемую сборку PIA как необходимый компонент. Дополнительные сведения см. в разделе [необходимые компоненты для развертывания решения Office](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understanding-the-client-profile"></a>Основные сведения о клиентском профиле  
 Клиентский профиль .NET Framework — это подмножество полной платформы .NET Framework. Если необходимо использовать только клиентские возможности платформы .NET Framework и требуется обеспечить наиболее быстрый режим развертывания для решения Office, то можно использовать клиентский профиль .NET Framework. Дополнительные сведения см. в разделе [Клиентский профиль .NET Framework](/dotnet/framework/deployment/client-profile).  
  
 При создании проекта Office, ориентированного на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], по умолчанию используется [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]. Если необходимо выполнить разработку для полной платформы [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], необходимо установить этот параметр после создания проекта. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="creating-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Создание решений для 64-разрядного выпуска Microsoft Office  
 Microsoft Office доступен в 64- и 32-разрядном выпусках. Для создания решений Office, которые могут выполняться в любом выпуске, целевой платформы для проекта должно быть присвоено **любой ЦП**. Это значение по умолчанию для проектов Office. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
 Существуют отдельные 64- и 32-разрядная версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которые используются в 64- и 32-разрядном выпусках Microsoft Office. Дополнительные сведения см. в разделе [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Сборки в решениях Office  
 При создании проекта Office с помощью средств разработки решений на базе Office в Visual Studio разрабатываемый код в конечном итоге компилируется в сборку. Обычно сборка развертывается на общем сервере или в каталоге на клиентском компьютере.  
  
 Сборки в решениях Office загружаются приложением Office. После загрузки сборки код в сборке может отвечать на события, возникающие в приложении, например, если пользователь выбирает пункт меню. Код в сборке также может вызывать объектную модель для автоматизации и расширения приложения. Кроме того, он может использовать любой из классов в [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md) и [надстроек VSTO архитектура](../vsto/architecture-of-vsto-add-ins.md).  
  
 Для обозначения сборки решения Office используют манифесты развертывания и манифесты приложения. Манифесты содержат такие сведения как имя, версия и расположение сборки, чтобы приложение могло найти, установить связь со сборкой и запустить нужную сборку. Для получения дополнительной информации см. [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Кроме сборки, проекты уровня документа содержат документ. Документ выступает в качестве внешнего интерфейса приложения и находится там, где происходит все взаимодействие с пользователем. С каждым документом может быть связана только одна основная сборка проекта. Однако на одну и ту же сборку могут указывать несколько документов.  
  
 Сборки в проектах уровня документа не внедряются в документ. Они хранятся в другом месте и обозначаются манифестом приложения документа.  
  
## <a name="security-considerations-for-assemblies"></a>Вопросы безопасности для сборок  
 Чтобы решение Office могло работать на компьютере, сборки, используемые решением, должны иметь необходимый уровень доверия для выполнения. Дополнительные сведения о безопасности см. в разделе [обеспечение безопасности решений Office](../vsto/securing-office-solutions.md).  
  
 По умолчанию сборка решения и любые связанные сборки, которые находятся в выходной папке вашего проекта, имеют необходимый уровень доверия для запуска на компьютере разработчика при сборке проекта. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
 По соображениям безопасности проекты рекомендуется создавать на своем локальном компьютере, а не в общей папке. Дополнительные сведения см. в разделе [совместная разработка решений Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Связанные сборки  
 Сборка может ссылаться на другие сборки, которые указаны в ссылках проекта. Однако одна сборка проекта уровня документа не может ссылаться на другую сборку проекта уровня документа.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Свойства в проектах Office](../vsto/properties-in-office-projects.md)   
 [Запуск решений в различных версиях Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Как: настроить сведения о конфигурации для решения Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [С помощью функциональных возможностей Office в Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  