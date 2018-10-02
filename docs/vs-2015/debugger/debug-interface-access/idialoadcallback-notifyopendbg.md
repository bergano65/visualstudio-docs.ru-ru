---
title: IDiaLoadCallback::NotifyOpenDBG | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b28b6a6ce52fa278ce19f6cdc9ec4346770b6a3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572681"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaLoadCallback::NotifyOpenDBG](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-notifyopendbg).  
  
Вызывается, когда был открыт файл .dbg кандидатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dbgPath`  
 [in] Полный путь файла .dbg.  
  
 `resultCode`  
 [in] Код, который указывает на успешное завершение (`S_OK`) или Ошибка загрузки применительно к этому файлу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата, обычно учитывается.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



