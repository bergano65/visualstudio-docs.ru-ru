---
title: IDebugExpressionEvaluator2::Terminate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Terminate
- IDebugExpressionEvaluator2::Terminate
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ef5f17354e45327a87ee77e5b437409719094e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678323"
---
# <a name="idebugexpressionevaluator2terminate"></a>IDebugExpressionEvaluator2::Terminate
Останавливает и удаляет средство оценки выражений.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Terminate (
    void
);
```

```csharp
int Terminate ();
```

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Сообщает средство оценки выражений, когда он выполняется очистка.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **ExpressionEvaluatorPackage** объекта, который предоставляет [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) интерфейс.

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)
{
    // scan the namespaces contained and delete
    EEExtensionMethodCache **ppChild = NULL;
    m_HashExtensionMethodCache.ResetHashIterator();
    while (ppChild = m_HashExtensionMethodCache.IterateHash())
    {
        delete *ppChild;
    }
    return VBEEImplicitVariables::Terminate();
}
```

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
