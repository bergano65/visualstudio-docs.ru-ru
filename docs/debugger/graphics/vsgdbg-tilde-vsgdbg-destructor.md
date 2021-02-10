---
title: VsgDbg::~VsgDbg (деструктор) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861352"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
Уничтожает экземпляр класса `VsgDbg`. В случае интенсивной записи графических сведений файл журнала графики завершается и закрывается, а ресурсы, которые использовались при активном захвате графических данных, освобождаются.

## <a name="syntax"></a>Синтаксис

```C++
~VsgDbg();
```

## <a name="see-also"></a>См. также
- [VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)