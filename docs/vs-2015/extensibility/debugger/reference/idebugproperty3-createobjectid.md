---
title: 'IDebugProperty3:: Креатеобжектид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842485"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает уникальный идентификатор для этого свойства, чтобы убедиться, что он уникален для всех остальных свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается, когда диспетчер отладки сеанса хочет убедиться, что это свойство однозначно идентифицируется всеми другими свойствами. Модуль отладки (DE) поддерживает этот метод, если только свойства, с которыми он работает, уже определены уникальным образом. Если параметр DE не поддерживает этот метод, он возвращает `E_NOTIMPL` .  
  
 Любой уникальный идентификатор, созданный с помощью `CreateObjectID` , уничтожается при вызове метода [дестройобжектид](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) . Кроме того, он сигнализирует об окончании потребности в уникальном определении этого свойства.  
  
> [!NOTE]
> Не существует метода для получения этого уникального идентификатора, поэтому при вызове метода DE может выполнять любые необходимые действия для уникальных идентификаторов `CreateObjectID` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
