---
title: AddMessage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896360"
---
# <a name="addmessage"></a>AddMessage
Добавляет пользовательское сообщение на головной дисплей (*HUD*) диагностики графики.

## <a name="syntax"></a>Синтаксис

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Параметры
 `szMessage` Сообщение, добавляемое на HUD.

## <a name="remarks"></a>Примечания
 Головной дисплей (HUD) диагностики графики отображается в левом верхнем углу приложения, которое работает в режиме диагностики графики. На нем отображаются сведения о приложении во время выполнения и о захвате данных графики, а также сообщения, добавленные путем вызова этой функции.

 Чтобы добавить сообщение на HUD, необязательно вести активный захват данных графики: сообщение можно добавить посредством экземпляра класса `VsgDbg`, но без предварительного вызова функции-члена [Init](init.md). Сообщения только отображаются на HUD; в файл журнала графики они не записываются.