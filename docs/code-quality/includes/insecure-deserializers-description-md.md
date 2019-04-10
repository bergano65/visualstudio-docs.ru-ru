---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367272"
---
Небезопасных deserializers уязвимы при десериализации ненадежных данных. Злоумышленник может изменить сериализованные данные для включения Непредвиденная типов с вредоносных побочными эффектами. Атак против небезопасных десериализатор может, например, выполнять команды от базовой операционной системы, обмениваться данными по сети или удалить файлы.