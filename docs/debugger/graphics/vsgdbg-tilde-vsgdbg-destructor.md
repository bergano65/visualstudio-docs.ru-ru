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
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734796"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Уничтожает экземпляр класса `VsgDbg`. Если сведения о графике записываются, файл журнала графики завершается и закрывается, а ресурсы, которые использовались при активной записи графических данных, освобождаются.

## <a name="syntax"></a>Синтаксис

```C++
~VsgDbg();
```

## <a name="see-also"></a>См. также
- [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)