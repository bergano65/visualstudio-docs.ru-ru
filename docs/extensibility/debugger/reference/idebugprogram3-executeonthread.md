---
title: IDebugПрограмма3::ExecuteonThread Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722656"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Выполняет программу отладчика. Поток возвращается, чтобы дать отладчику информацию о том, какой поток просматривает пользователь при выполнения программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`\
(в) Объект [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Существует три способа возобновления выполнения отладчика после остановки:

- Выполнение: Отмена любого предыдущего шага и выполнение до следующего брейк-пойнта и так далее.

- Шаг: Отмена любого старого шага и запуск до завершения нового шага.

- Продолжить: Выполнить еще раз, и оставить любой старый шаг активным.

  Передаваемый поток `ExecuteOnThread` полезен при принятии решения о том, какой шаг следует отменить. Если вы не знаете поток, выполнение выполнения отменяет все шаги. Зная поток, достаточно отменить шаг на активном потоке.

## <a name="see-also"></a>См. также
- [Выполнить](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
