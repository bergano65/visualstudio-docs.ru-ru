---
title: Создание проекта облачной службы с помощью Visual Studio | Документация Майкрософт
description: Узнайте, как создать проект облачной службы Azure с помощью Visual Studio
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003027"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Создание проекта облачной службы с помощью Visual Studio
Инструменты Azure для Visual Studio предоставляют шаблон проекта, которая позволяет создавать [облачной службы Azure](/azure/cloud-services/cloud-services-choose-me), это простой службы Azure общего назначения. После создания проекта Visual Studio предоставляет возможность настройки, отладки и развертывания облачной службы в Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Шаги по созданию проекта облачной службы в Visual Studio
В этом разделе описывается создание проекта облачной службы в Visual Studio с помощью одного или нескольких веб-ролей.  

1. Запустите Visual Studio с правами администратора.

1. В главном меню выберите **файл** > **New** > **проекта**.

1. Выберите **Cloud** из визуального C# или Visual Basic в узлах шаблонов проектов и выберите **облачной службы Azure** из списка шаблонов.

    ![Новая облачная служба Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Укажите, какая версия .NET Framework, вы хотите использовать для разработки проекта.

1. Введите имя и расположение проекта и имя для решения. 

1. Нажмите кнопку **ОК**.

1. В **новая облачная служба Microsoft Azure** диалоговом окне выберите роли, которые вы хотите добавить и нажмите кнопку со стрелкой вправо, чтобы добавить их в решение.

    ![Выберите новый ролей облачной службы Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Чтобы переименовать добавленную роль, наведите указатель мыши на роль в **новая облачная служба Microsoft Azure** диалоговое окно и в контекстном меню выберите **Переименовать**. Вы также можете переименовать роль в решении (в **обозревателе решений**) после его добавления.

    ![Переименование роли облачной службы Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Проект Azure для Visual Studio имеет связи с проектами ролей в решении. Проект также включает *файл определения службы* и *файл конфигурации службы*:

- **Файл определения службы** -определяет параметры среды выполнения для приложения, включая какие роли являются обязательными, конечные точки и размер виртуальной машины. 
- **Файл конфигурации службы** — настраивает количество экземпляров роли являются выполнения и значения параметров, определенных для роли. 

Дополнительные сведения об этих файлах см. в разделе [Настройка ролей для облачной службы Azure с помощью Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Следующие шаги
- [Управление ролями в проекты облачных служб Azure с помощью Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
