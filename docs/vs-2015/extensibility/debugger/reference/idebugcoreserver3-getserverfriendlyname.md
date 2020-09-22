---
title: 'IDebugCoreServer3:: Жетсерверфриендлинаме | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa81daf7ab1d592e6a2cd460268e5d66925f61e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842509"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает понятное имя для сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 заполняет Возвращает понятное имя для сервера.  
  
> [!NOTE]
> Вызывающий объект отвечает за освобождение строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Для серверов, запускаемых пользователем, имя, возвращаемое этим методом, является полным именем сервера. Для автоматического запуска серверов используется имя компьютера, на котором запущен сервер.  
  
 Для имени, ориентированного на компьютер, вызовите метод- [ServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [Имя_сервера](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
