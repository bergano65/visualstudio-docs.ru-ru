---
title: Диалоговое окно "Параметры", "Проекты и решения", "Веб-проекты" | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.WebProjects
ms.assetid: ea813046-1ae6-4c9f-9784-dc41494101b9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90da4845ca5edcf68a977ea79a73e06fa4c4455b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917674"
---
# <a name="options-dialog-box-projects-and-solutions-web-projects"></a>«Диалоговое окно параметров», «Проекты и решения», «Веб-проекты»
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает веб-сервер, который будут использовать веб-проекты для разработки в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Чтобы получить доступ к этому диалоговому окну, выберите **Сервис > Параметры**. Разверните узел **Проекты и решения** и выберите **Веб-проекты**.

 По умолчанию при запуске веб-проекта в Visual Studio (например, с помощью F5 или CTRL + F5) система Visual Studio использует Visual Studio Development Server. Дополнительные сведения см. в разделе [Веб-серверы в Visual Studio для веб-проектов ASP.NET](https://msdn.microsoft.com/31d4f588-df59-4b7e-b9ea-e1f2dd204328).

> [!NOTE]
> Доступные в диалоговых окнах параметры, а также названия и расположение команд меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Эта страница справки была написана с учетом **веб-параметров**. Чтобы просмотреть или изменить настройки, выберите **Настройки импорта и экспорта** в меню **Сервис**. Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Параметры
 **Использовать 64-разрядную версию IIS Express для веб-сайтов и проектов** Выберите этот параметр, чтобы использовать IIS Express вместо Visual Studio Development Server. Дополнительные сведения см. в разделе [Introducing IIS Express](https://weblogs.asp.net/scottgu/introducing-iis-express) (Знакомство с IIS Express) и [IIS Express Overview](/iis/extensions/introduction-to-iis-express/iis-express-overview) (Обзор IIS Express). Этот параметр отключен по умолчанию.

 **Предупреждать перед запуском веб-приложений, если в списке ошибок есть ошибки** Если этот флажок установлен, вы получите предупреждение при попытке запустить веб-приложение, если оно не будет скомпилировано без ошибок.
