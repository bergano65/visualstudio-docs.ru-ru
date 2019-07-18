---
title: Интерфейс IWebAppDiagnosticsObjectInitialization | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443682"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization — интерфейс
Этот интерфейс можно реализовать в классах, реализующих [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Интерфейс IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется объектом, который реализует [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md). В большинстве случаев этот объект является PDM.  
  
 После создания объекта [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) вызывается со ссылкой на приложения отладки PDM и `hPassToObject` параметр `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Инициализирует объект.|