---
title: Отправка задания для обучения модели в Azure Batch AI
description: обучение модели в облаке
keywords: ии, visual studio, обучение модели, облако
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: ec0db69bbde1e2abab7022759ed0f7a3d2a88530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Обучение моделей искусственного интеллекта в Azure Batch AI

Batch AI — это облачная служба, позволяющая специалистам по искусственному интеллекту и обработке и анализу данных обучать искусственный интеллект и другие модели машинного обучения в кластерах виртуальных машин Azure, включая виртуальные машины с поддержкой GPU. Вы описываете требования задания, расположение входных данных, место сохранения выходных данных, а служба Batch AI делает все остальное. [Подробнее об Azure Batch AI](https://docs.microsoft.com/azure/batch-ai/overview)

Служба интегрирована с инструментами Visual Studio для сценариев ИИ, поэтому вы можете динамически масштабировать модели обучения в Azure.  После [установки инструментов Visual Studio для сценариев ИИ](installation.md) вы можете легко создать проект Python с помощью готовых рецептов из коллекции примеров машинного обучения Azure.

1. Запустите Visual Studio. Откройте **обозреватель сервера**, открыв меню **Инструменты ИИ** и выбрав пункт **Выбрать кластер**

    ![Выбор кластера](media\train-model\select-cluster.png)


2. Разверните узел **Инструменты ИИ**. Все имеющиеся ресурсы Batch AI будут автоматически обнаружены и отобразятся в обозревателе сервера.

    ![Коллекция примеров](media\train-model\batchai.png)

3. Последовательно выберите **"Вид" > "Team Explorer…"**, чтобы открыть окно **Team Explorer**, в котором вы можете подключиться к GitHub или Visual Studio Team Services либо клонировать репозиторий.

    ![Окно Team Explorer с возможностями подключения к Visual Studio Team Services и GitHub, а также клонирования репозитория](media\train-model\team-explorer.png)

4. В разделе **Локальные репозитории Git** в поле URL-адреса введите `https://github.com/Microsoft/samples-for-ai`, укажите папку для клонируемых файлов и нажмите кнопку **Клонировать**.

    > [!Tip]
    > В папку, указанную в Team Explorer, будут приниматься клонируемые файлы. В отличие от использования команды `git clone`, при клонировании в Team Explorer не создается автоматически вложенная папка с именем репозитория.

5. По завершении клонирования выберите **Файл > Открыть решение > Решение или проект**.

    ![Коллекция примеров](media\train-model\open-solution.png)

5. Откройте файл **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** в каталоге, в который был клонирован репозиторий.

    ![Коллекция примеров](media\train-model\tensorflowexamples.png)

5. Задайте проект MNIST в качестве **запускаемого проекта**.

    ![Коллекция примеров](media\train-model\mnist-startup.png)

1. **Щелкните правой кнопкой мыши** проект MNIST и выберите пункт **Отправить задание**.

    ![Коллекция образцов](media\train-model\submit-job.png)

1. Выберите кластер **Azure Batch AI** и нажмите кнопку **Импорт**. Выберите файл `AzureBatchAI_TF_MNIST.json`, чтобы быстро задать значения по умолчанию, например используемый образ Docker. Нажмите кнопку **Отправить**.

    ![Коллекция примеров](media\train-model\submit-batch.png)