---
title: AddMessage | Документация Майкрософт
description: Используйте метод AddMessage класса VsgDbg для добавления пользовательского сообщения на головной дисплей (HUD) диагностики графики.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874643"
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