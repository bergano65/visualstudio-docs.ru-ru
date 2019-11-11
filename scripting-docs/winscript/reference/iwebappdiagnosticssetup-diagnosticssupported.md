---
title: Ивебаппдиагностикссетуп::D Иагностикссуппортед | Документация Майкрософт
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
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984573"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Определяет, поддерживаются ли в этом приложении средства диагностики. Если [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) был вызван для объекта, реализующего этот интерфейс со значением, ОТЛИЧНЫМ от NULL, [диагностикссуппортед](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. В противном случае возвращается `false` и вызовы [ивебаппдиагностикссетуп:: креатеобжектвисситеатвебапп](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются ошибкой.  
  
> [!IMPORTANT]
> [Интерфейс ивебаппдиагностикссетуп](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Найдено в activdbg100.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 Если [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) был вызван для объекта, реализующего этот интерфейс со значением, ОТЛИЧНЫМ от NULL, [диагностикссуппортед](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает `true`. В противном случае возвращается `false`, а вызовы [ивебаппдиагностикссетуп:: креатеобжектвисситеатвебапп](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются ошибкой.