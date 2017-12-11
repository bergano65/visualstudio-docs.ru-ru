---
title: "Создание проекта в инструментах Visual Studio для сценариев ИИ"
description: "создание проекта с помощью примера из коллекции машинного обучения azure"
keywords: "ии, visual studio, машинное обучение azure"
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Создание проекта ИИ с помощью коллекции Машинного обучения Azure в Visual Studio

Машинное обучение Azure встроено в инструменты Visual Studio для сценариев ИИ. Вы можете использовать его для отправки заданий Машинного обучения в удаленные вычислительные целевые объекты, такие как виртуальные машины Azure, кластеры Spark и многие другие. Дополнительные сведения об [Экспериментировании в Машинном обучении Azure](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

После [установки инструментов Visual Studio для сценариев ИИ](installation.md) можно легко создать проект Python с помощью готовых рецептов из коллекции образцов машинного обучения Azure.

> ! Нужно установить Azure Machine Learning Workbench. Для этого ознакомьтесь с разделом [Краткое руководство по установке машинного обучения Azure](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) 

1. Запустите Visual Studio. Откройте **обозреватель сервера**, открыв меню **Инструменты ИИ** и выбрав пункт **Выбрать кластер**.  

    ![Выбор кластера](media\create-project\select-cluster.png)

1. Войдите в подписку на машинное обучение Azure, щелкнув правой кнопкой мыши узел **Машинное обучение Azure** в обозревателе сервера, выбрав пункт **Вход** и выполнив инструкции.

    ![вход](media\create-project\azureml-login.png)
 
2. Выберите **Средства ИИ > Коллекция образцов машинного обучения Azure**. 
    
    ![Коллекция образцов](media\create-project\gallery.png)

1. Для этого краткого руководства выберите образец **MNIST using TensorFlow** и нажмите кнопку **Установить**. Укажите следующие сведения: 
2.
 - **Группа ресурсов**: группа ресурсов Azure, в которой будут храниться метаданные
 - **Учетная запись**: учетная запись для экспериментов с Машинным обучением Azure
 - **Рабочая область**: рабочая область Машинного обучения Azure
 - **Тип проекта**: платформа машинного обучения. В этом случае выберите **TensorFlow**.
 - **Добавить в решение**: определяет, следует ли добавить образец в текущее решение Visual Studio или создать и открыть новое решение
 - **Путь к проекту**: место, где будет сохранен код
 - **Имя проекта**: введите **TensorFlowMNIST**
   

    ![Итоговый проект при использовании шаблона приложения Python](media\create-project\new-AzureSampleProject.png)

1. Visual Studio создает файл проекта (файл `.pyproj` на диске) вместе с другими файлами, определенными в образце. В случае с шаблоном MNIST проект содержит несколько файлов.

    ![mnist](media\create-project\azml-mnist.png)

1. Отправьте задание в службу машинного обучения Azure. 

    ![mnist](media\create-project\submit-azml.png)

1. Запустите в контейнере Docker или на локальном компьютере.

    ![mnist](media\create-project\azml-local.png)