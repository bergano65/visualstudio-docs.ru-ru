---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по HeatmapScene в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f707052e0ec0b9cda60c111767800c1ce14d6103
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="heatmapscene-explanation"></a>Сведения о HeatmapScene

HeatmapScene содержит экземпляр готового блока **LevelGeometry**. Таким образом, загруженные из Azure координаты для сбоев правильно сопоставляются с коллекцией уровней.

## <a name="heatmap-script"></a>Скрипт тепловой карты

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` подключается к таблице CrashInfo в Azure и использует <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a>, чтобы добавить все ее записи в список.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` выполняет итерации по списку полученных из Azure сбоев и создает для каждой записи экземпляр готового блока маркера сбоя.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

`DeleteCrashDataAsync` вызывается, когда пользователь нажимает кнопку **Очистить данные**. Он выполняет итерации по локальному списку сбоев и вызывает <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> для каждой записи. При этом в столбце **Удалено** таблицы для каждой записи устанавливается значение **true**. `ToListAsync` пропускает эти удаленные записи.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Дальнейшие действия

* [Сведения о LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)