---
title: 'IDebugProgramPublisher2:: Унпублишпрограм | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05efc566cec0e7e885b16a4bb7c7e7d6256ac7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146284"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Делает программу недоступной для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDebuggeeInterface`  
 окне `IUnknown` Интерфейс программы. Это то же значение, которое передается в метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) и уникально идентифицирует удаляемую программу (то есть используется как файл cookie).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Чтобы сделать программу доступной для модулей отладки и диспетчера отладки сеансов, используйте метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
