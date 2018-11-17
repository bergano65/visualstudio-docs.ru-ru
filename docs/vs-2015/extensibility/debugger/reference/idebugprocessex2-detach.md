---
title: IDebugProcessEx2::Detach | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2848549a1640865296a64c88c4b54f89a57df2a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732806"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод сообщает процесс, что сеанс больше не является отладка процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSession`  
 [in] Значение, уникально идентифицирующий сеанс, чтобы отключить этот процесс из.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Переданный интерфейс `pSession` является следует рассматривать только как файл cookie, значение, однозначно определяющий диспетчер отладки сеансов, которые изначально подключен к этому процессу; ни один из методов предоставленного интерфейса являются рабочими.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

