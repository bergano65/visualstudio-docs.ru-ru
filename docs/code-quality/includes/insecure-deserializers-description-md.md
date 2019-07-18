---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147104"
---
Небезопасных deserializers уязвимы при десериализации ненадежных данных. Злоумышленник может изменить сериализованные данные для включения Непредвиденная типов для вставки объектов с помощью вредоносных побочные эффекты. Атак против небезопасных десериализатор может, например, выполнять команды от базовой операционной системы, обмениваться данными по сети или удалить файлы.