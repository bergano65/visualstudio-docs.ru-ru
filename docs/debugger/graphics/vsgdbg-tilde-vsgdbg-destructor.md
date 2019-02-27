---
title: 'VsgDbg:: ~ VsgDbg (деструктор) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64d2ce58a0a543a6bccfca4d96ff57915d45ce49
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686565"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Уничтожает экземпляр `VsgDbg` класса. Если активно идет запись графических данных, файл журнала графики является завершения и закрытия и освобождение ресурсов, которые были использованы при активный захват данных графики.

## <a name="syntax"></a>Синтаксис

```C++
~VsgDbg();
```

## <a name="see-also"></a>См. также раздел
- [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)