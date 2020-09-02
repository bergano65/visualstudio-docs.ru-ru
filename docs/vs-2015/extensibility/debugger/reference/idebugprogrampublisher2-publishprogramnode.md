---
title: IDebugProgramPublisher2::P Ублишпрограмноде | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eac08c35afe407358b7e2d37216dda202c490bd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146308"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Делает узел программы доступным для использования механизмами отладки (DEs) и диспетчером отладки сеансов (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```csharp  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProgramNode`  
 окне Объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющий узел программы, который нужно сделать доступным.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод позволяет программам запрашивать информацию, прежде чем выбирать и запускать их для отладки.  
  
 Чтобы удалить узел программы из уровня доступности, вызовите метод [унпублишпрограмноде](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
