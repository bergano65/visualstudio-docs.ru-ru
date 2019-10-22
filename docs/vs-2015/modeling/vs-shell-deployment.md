---
title: Развертывание оболочки VS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659303"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Изолированная оболочка позволяет определить, какие функциональные возможности Visual Studio необходимы для взаимодействия с конкретным доменным языком и как это решение должно отображаться. Дополнительные сведения о изолированной оболочке Visual Studio см. [в разделе Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md). Дополнительные сведения о настройке изолированной оболочки можно найти в статье [Настройка изолированной оболочки](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Установка оболочки Visual Studio в качестве целевого объекта развертывания

1. В проекте **DslPackage** откройте **source.extension.TT**.

2. В разделе `<SupportedProducts>` вставить:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Замените *мисолатедшелл* именем пакета изолированной оболочки.
