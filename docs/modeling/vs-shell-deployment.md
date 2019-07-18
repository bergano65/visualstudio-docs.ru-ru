---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934303"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированной оболочки позволяет определить, какие Visual Studio функциональные возможности, вам понадобится взаимодействовать с вашего доменного языка и как это решение должно выглядеть. Дополнительные сведения о изолированная оболочка Visual Studio, см. в разделе [Настройка изолированной оболочки](https://vspartner.com/pages/vsshells).

Чтобы задать оболочку Visual Studio в качестве цели развертывания:

1. В **DslPackage** откройте проект **source.extension.tt**.

2. В разделе `<SupportedProducts>` вставки:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *MyIsolatedShell* с именем пакета изолированной оболочки.