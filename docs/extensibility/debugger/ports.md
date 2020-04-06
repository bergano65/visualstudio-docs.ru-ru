---
title: Порты Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738303"
---
# <a name="ports"></a>порты;
В архитектуре отладчика *порт:*

- Является контейнером для набора процессов, работающих на сервере. Например, порт может представлять подключение к устройству на базе Windows CE серийным кабелем или к сетевой машине, не являющихся DCOM. Один специальный порт, называемый местным портом, содержит все процессы, работающие на локальной машине.

- Может идентифицировать себя по имени или идентификатору.

- Можно перечислить все процессы, работающие в порту, запуск и прекращение этих процессов.

- Представлен интерфейсом [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) который создается путем передачи аргумента [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) [в AddPort.](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поставляет порт по умолчанию, который обрабатывает все процессы на основе Windows, как родные, так и управляемые. Пользовательский порт должен быть настроен для соединения с внешними устройствами, которые не основаны на Windows. Для поставки таких пользовательских портов, вы также должны настроить пользовательский поставщик порта.

## <a name="see-also"></a>См. также
- [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Процессов](../../extensibility/debugger/processes.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
