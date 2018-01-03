---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по модели данных в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 57a6a6aaff1c41a8720f842e20142e3cb1a2e538
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="create-data-model-classes"></a>Создание классов моделей данных

Проект Unity должен содержать классы моделей данных, которые соответствуют таблицам, созданным в интерфейсе мобильных приложений Azure.

## <a name="create-the-crashinfo-class"></a>Создание класса CrashInfo

1. В Unity добавьте новую папку с именем **Scripts** в корневом каталоге **Assets**. Внутри новой папки Scripts создайте еще одну папку с именем **Data Models** (только для организаций).

2. Внутри новой папки Data Models создайте скрипт C# с именем **CrashInfo**.

3. Откройте новый скрипт `CrashInfo`, удалите весь код шаблона, включая объявление класса и операторы using, и добавьте следующий код:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Для правильной работы примера имя класса модели данных должно совпадать с именем простой таблицы, созданной в интерфейсе мобильных приложений Azure.

## <a name="create-the-highscoreinfo-class"></a>Создание класса HighScoreInfo

1. Внутри папки Data Models создайте скрипт C# с именем **HighScoreInfo**.

2. Откройте новый скрипт `HighScoreInfo`, удалите весь код шаблона, включая объявление класса и операторы using, и добавьте следующий код:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Дальнейшие действия

  * [Реализация Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
