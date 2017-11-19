---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5706d868f0096d486629c18c3d700349af92cc92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Определяет, поддерживаются ли диагностики в этом приложении. Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван для объекта, реализующего этот интерфейс со значением НЕНУЛЕВОЙ [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. Если нет, она возвращает `false` и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.  
  
> [!IMPORTANT]
>  [Iwebappdiagnosticssetup — интерфейс](../../winscript/reference/iwebappdiagnosticssetup-interface.md) — реализованный PDM v11.0 и более поздней версии. Найти в activdbg100.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван для объекта, реализующего этот интерфейс со значением НЕНУЛЕВОЙ [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. Если нет, она возвращает `false`и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.