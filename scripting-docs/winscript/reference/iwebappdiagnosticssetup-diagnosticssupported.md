---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d4214dea16c1e8a96ece7428f9ea73640025a9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443671"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Определяет, поддерживаются ли диагностики в это приложение. Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван для объекта, реализующего этот интерфейс со значением отличное от NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. Если нет, он возвращает `false` и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.  
  
> [!IMPORTANT]
> [Интерфейс IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) является реализуется PDM v11.0 и более поздней версии. Найти в activdbg100.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван для объекта, реализующего этот интерфейс со значением отличное от NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. Если нет, он возвращает `false`, а также вызовы к [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.