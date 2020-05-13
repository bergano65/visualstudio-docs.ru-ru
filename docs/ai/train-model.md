---
title: Отправка задания для обучения модели в Azure Batch AI
description: обучение модели в облаке
keywords: ии, visual studio, обучение модели, облако
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 083b2cb191d627ced936ead6a90b363970a9e7e0
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638776"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Обучение моделей искусственного интеллекта в Azure Batch AI

Batch AI — это управляемая служба, которая позволяет специалистам по обработке и анализу данных и исследователям искусственного интеллекта (ИИ) обучать модель ИИ и другие модели машинного обучения на кластерах виртуальных машин Azure, в том числе виртуальных машин с поддержкой GPU. Вы описываете требования своего задания, где можно найти входные данные и куда сохранить выходные данные, а Batch AI выполняет все остальное. [Подробнее об Azure Batch AI](/azure/batch-ai/overview)

Служба интегрирована с инструментами Visual Studio для сценариев ИИ, поэтому вы можете динамически масштабировать модели обучения в Azure.  После [установки инструментов Visual Studio для сценариев ИИ](installation.md) можно легко создать проект Python с помощью готовых рецептов из коллекции образцов машинного обучения Azure.

1. Запустите Visual Studio. Откройте **обозреватель сервера**, открыв меню **Инструменты ИИ** и выбрав пункт **Выбрать кластер**.

    ![Выбор кластера](media/train-model/select-cluster.png)

2. Разверните узел **Инструменты ИИ**. Все имеющиеся ресурсы Batch AI будут автоматически обнаружены и отобразятся в обозревателе сервера.

    ![Коллекция примеров](media/train-model/batchai.png)

3. Последовательно выберите **Вид > Team Explorer**, чтобы открыть окно **Team Explorer**, в котором вы можете подключиться к GitHub или Azure DevOps либо клонировать репозиторий.

    ![Окно Team Explorer с возможностями подключения к Azure DevOps и GitHub, а также клонирования репозитория](media/train-model/team-explorer-devops.png)

4. В разделе **Локальные репозитории Git** в поле URL-адреса введите `https://github.com/Microsoft/samples-for-ai`, укажите папку для клонируемых файлов и нажмите кнопку **Клонировать**.

    > [!Tip]
    > В папку, указанную в Team Explorer, будут приниматься клонируемые файлы. В отличие от использования команды `git clone`, при клонировании в Team Explorer не создается автоматически вложенная папка с именем репозитория.

5. По завершении клонирования выберите **Файл > Открыть решение > Решение или проект**.

    ![Коллекция примеров](media/train-model/open-solution.png)

6. Откройте файл **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** в каталоге, в который был клонирован репозиторий.

    ![Коллекция примеров](media/train-model/tensorflowexamples.png)

7. Задайте проекту MNIST параметр **Запускаемый проект**

    ![Коллекция примеров](media/train-model/mnist-startup.png)

8. <strong>Щелкните правой кнопкой мыши **проект MNIST** и выберите пункт **Отправить задание**</strong>

    ![Коллекция примеров](media/train-model/submit-job.png)
9. Выберите кластер **Azure Batch AI** и нажмите кнопку **Импорт**. Выберите файл `AzureBatchAI_TF_MNIST.json`, чтобы быстро задать значения по умолчанию, например используемый образ Docker. Теперь нажмите кнопку **Submit**(Отправить).

    ![Коллекция примеров](media/train-model/submit-batch.png)
