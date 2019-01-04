---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 2d732b050a9f12b6324abaf253739cd4f3e223aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914492"
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