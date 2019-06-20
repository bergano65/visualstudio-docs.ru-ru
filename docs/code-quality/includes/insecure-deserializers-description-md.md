---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2019
ms.locfileid: "67254183"
---
Небезопасных deserializers уязвимы при десериализации ненадежных данных. Злоумышленник может изменить сериализованные данные для включения Непредвиденная типов для вставки объектов с помощью вредоносных побочные эффекты. Атак против небезопасных десериализатор может, например, выполнять команды от базовой операционной системы, обмениваться данными по сети или удалить файлы.