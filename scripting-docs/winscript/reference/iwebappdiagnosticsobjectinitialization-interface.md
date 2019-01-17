---
title: Интерфейс IWebAppDiagnosticsObjectInitialization | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c892d3eceea65f16c69bfd2202b1f64181773532
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348052"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization — интерфейс
Этот интерфейс можно реализовать в классах, реализующих [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Интерфейс IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется объектом, который реализует [интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md). В большинстве случаев этот объект является PDM.  
  
 После создания объекта [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) вызывается со ссылкой на приложения отладки PDM и `hPassToObject` параметр `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Инициализирует объект.|