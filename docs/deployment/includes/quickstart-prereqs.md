---
ms.openlocfilehash: 034d4c1e528ff33343b6da1dab3a2de96a0228fc
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70197178"
---
## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), установленная с соответствующими рабочими нагрузками для выбранного языка:
  * ASP.NET: **ASP.NET и веб-разработка**
  * Python: **Разработка на Python**
  * Node.js: **Разработка для Node.js**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), установленная с соответствующими рабочими нагрузками для выбранного языка:
  * ASP.NET: **ASP.NET и веб-разработка**
  * Python: **Разработка на Python**
  * Node.js: **Разработка для Node.js**
::: moniker-end

* Проект ASP.NET, ASP.NET Core, Python или Node.js. Если у вас еще нет проекта, выберите приведенный ниже параметр:
  * ASP.NET Core: Выполните инструкции в статье [Краткое руководство: создание первого веб-приложения ASP.NET Core с помощью Visual Studio](../../ide/quickstart-aspnet-core.md) или выберите **Файл** > **Создать проект**, затем выберите **Visual C#**  >  **.NET Core**, после чего щелкните **Веб-приложение ASP.NET Core**. При появлении запроса выберите шаблон **Веб-приложение (модель-представление-контроллер)** , убедитесь, что выбран параметр **Без проверки подлинности**, после чего нажмите кнопку **ОК**.
  * Python: Выполните инструкции в статье [Краткое руководство: создание первого веб-приложения Python с помощью Visual Studio](../../ide/quickstart-python.md) или выберите **Файл** > **Создать проект**, **Python** и затем — **Веб-проект Flask**.
  * Node.js: Выполните инструкции в статье [Краткое руководство: создание первого приложения Node.js с помощью Visual Studio](../../ide/quickstart-nodejs.md) или выберите **Файл** > **Создать проект**, затем **JavaScript**, после чего выберите пункт **Пустое веб-приложение Node.js**.

* Прежде чем выполнять действия по развертыванию, выполните сборку проекта с помощью команды **Сборка > Построить решение**.