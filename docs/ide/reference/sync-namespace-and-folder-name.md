---
title: Синхронизация пространства имен и имени папки
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для синхронизации пространства имен и имени папки.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e4f10f3555f4edcec031cd4c144bf5a28e9c055d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967154"
---
# <a name="sync-namespace-and-folder-name"></a>Синхронизация пространства имен и имени папки

Область применения этого рефакторинга:

- C#

**Что?** Синхронизация пространства имен и имени папки.

**Когда?** Вы хотите перепроектировать части решения, перетащив файл в новую папку. 

**Зачем?** Вы хотите убедиться, что ваше пространство имен соответствует вашей новой структуре папок.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в имени пространства имен.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите команду **Изменить пространство имен на \<folder name>** .

   ![Синхронизация пространства имен и имени папки](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
