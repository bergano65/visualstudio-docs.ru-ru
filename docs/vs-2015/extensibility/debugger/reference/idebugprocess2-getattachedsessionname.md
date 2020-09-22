---
title: 'IDebugProcess2:: Жетаттачедсессионнаме | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3acc40e2b906bd46b832d9fa11578de346014042
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842472"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя сеанса, в котором выполняется отладка этого процесса. Интегрированная среда разработки может отображать эту информацию для пользователя, выполняющего отладку определенного процесса на определенном компьютере.  
  
> [!NOTE]
> Этот метод является устаревшим, и его реализация всегда должна возвращать `E_NOTIMPL` .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод всегда должен возвращать `E_NOTIMPL` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
