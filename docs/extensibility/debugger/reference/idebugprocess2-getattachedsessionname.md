---
title: IDebugProcess2::GetAttachedSessionName | Документация Майкрософт
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
ms.openlocfilehash: cd927d66db6e38e3a208cac1ca6545a5b290dc03
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413487"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает имя сеанса, который выполняет отладку этого процесса. Интегрированная среда разработки для отображения этой информации для пользователя, который выполняет отладку определенного процесса на конкретном компьютере.  
  
> [!NOTE]
> Этот метод является устаревшим, и ее реализация должна всегда возвращать `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод должен всегда возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
