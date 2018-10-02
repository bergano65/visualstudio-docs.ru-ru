---
title: IDebugProgram2::Terminate | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05edc99dcb408159966f08a3d38f6663f73f290
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563926"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgram2::Terminate](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-terminate).  
  
Завершает программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если это возможно программа будет завершен и выгружать из процесса; в противном случае модуль отладки (DE) выполнит необходимые операции очистки.  
  
 Этот метод или [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) метод вызывается средой IDE, обычно в ответ на пользователя к остановке всех отладки. Реализация этого метода в идеале, завершение работы программы в рамках процесса. Если это невозможно, DE следует привести программы к работе в этом процессе большее количество (и выполнить необходимую очистку). Если `IDebugProcess2::Terminate` метод был вызван в интегрированной среде разработки, весь процесс завершается через некоторое время после `IDebugProgram2::Terminate` вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

