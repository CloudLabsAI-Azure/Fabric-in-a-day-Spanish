

# 目录

- **简介**	

- **实验凭据**
	
- **导入数据流模板：**

  - 如何导入数据流模板	

- **演示要求**	

- **环境**

   - 如何配置实验环境	

   - 如何为预测创建笔记本	


# 简介

本文档提供了以下功能的指南：

- 实验凭据
- 如何导入数据流模板
- 如何加载 Spark 库并配置环境
- 如何创建笔记本
- 如何使用数据科学模型创建预测
- 如何将输出保存到语义模型

**免责声明:** 请注意，由于产品每天都在变化，某些屏幕截图可能已过时。我们将努力在下次更新中进行修复。

# 实验凭据：

如果任何参与者选择在替代环境中完成实验，以下是您可能需要共享的凭据。
参与者需要使用与其实验帐户关联的用户名和密码连接到 Dataverse 和 SharePoint

Snowflake 用户名：**TE_SNOWFLAKE**

Snowflake 密码：**8UpfRpExVDXv2AC**

ADLS Gen2 帐户密钥：**Lpwn8hQASMpe5r4F+VFXAvpnzKF9x9Kjt5GMvMCFWB0xCFuM4fyVwOW6rF200bTop3LpKpsIno/T+AStx6cz6w==**
 
# 导入数据流模板：

作为讲师，您可以选择让参与者可以选择导入数据流模板。以下是导入模板的步骤。

## 如何导入数据流模板
1. 导航到**您在实验 2 任务 8 中创建并命名为 FAIAD_ <username> 的 Fabric** **工作区。** 我们自己的命名为 FAIAD_demouser
2. 导航到 **Data Factory 主页**页面。
3. 在菜单中，选择**新建 -> 数据流 Gen2**
 
4. Power Query 窗口随即打开。在中间窗格中，选择**从 Power Query** **模板导入。**
 
5. 浏览到**桌面 -> 解决方案**文件夹，并选择您要导入的数据流。这里我们导入 **df_People_SharePoint.pqt**
6. 选择**打开。**

导入后，请注意查询以及查询的所有步骤均已导入。但是，您需要配置连接。此外还需要设置数据目标。请按照实验说明完成这些步骤。
 

# 演示要求

您（讲师）需要完成实验 1-6，并在进入后续步骤之前获取所有数据。

# 环境

**如何配置实验环境**

**注意：** 建议在演示之前配置实验环境，因为安装库需要时间。您可以引导参与者完成这些步骤。

7. 导航到**您在实验 2 任务 8 中创建并命名为 FAIAD_\<username> 的 Fabric 工作区**
8. 从菜单中选择**省略号 (…)。**
9. 选择**工作区设置。**
 
10. “工作区设置”对话框随即打开。从左侧菜单中展开**数据科学/工程。**

11. 选择 **Spark 设置。**
12. 从 Spark 设置菜单中，选择**环境**选项卡。

13. 将**设置默认环境**滑块切换到**开。**
14. 选择**工作区默认值**下拉列表。
15. 选择**新建环境。**
 
16. “新建环境”对话框随即打开。在名称中输入 **FAIAD_\<username>_env**

    **注意：** 工作区名称必须唯一。我们使用 FAIAD_demouser_env 作为本文档的工作区名称。但是，您必须使用不同的工作区名称。确保“名称”字段下方显示带有 **“此名称可用”** 的绿色复选标记。

17. 选择**创建。**
 
18. 您将导航到添加公共和自定义库的屏幕。我们要添加的是 Prophet，这是一个公共库。从顶部菜单中选择**公共库 -> 从 PyPI 添加**

19. 在中间窗格中“库”下的文本框中输入 **prophet**

    **注意：** 确保**版本为 1.1.5**

20. 从右侧窗格中，选择**发布。**
 
21. “挂起的更改”对话框随即打开。选**择全部发布。**
22. “发布所有更改？”对话框随即打开。选择**发布。** 发布更新需要几分钟。
 
23. 选择**查看进度**以检查进度。发布更新需要几分钟。
 
24. 安装后，注意**状态**会更改为**成功。**
 
25. 现在我们已经配置了环境，我们必须将其保存为工作区的默认环境。从左侧面板中，选择 **FAIAD_\<username>**

26. 从顶部菜单中，选择**工作区设置**（或省略号 -> 工作区设置）。
 
27. “工作区设置”对话框随即打开。从左侧菜单中展开**数据工程/科学。**
28. 选择 **Spark 设置。**
29. 从 Spark 设置菜单中，选择选项卡**环境。**
30. 将**设置默认环境滑块切换到开。**
31. 选择工作区默认值下拉列表。
32. 从下拉列表中选择您刚刚创建的环境：**FAIAD_\<username>_env**
33. 选择**保存。**
 

## 如何为预测创建笔记本

34. 导航到 **Synapse Data Engineering 主页**页面。
35. 选择**新建 -> 笔记本**。
 
36. 提供布局的**简要概述**：笔记本、语言、环境、如何创建新单元格等。
37. 创建**新单元格**。
38. 输入以下**代码**：

        ```
        from pyspark.sql import SparkSession
        from pyspark.sql.functions import month, year, col
        from prophet import Prophet
        import pandas as pd

        # Initialize Spark session
        spark = SparkSession.builder.appName("Prophet Forecasting").getOrCreate()

        # Load data from your specific Spark table
        df = spark.sql("SELECT * FROM lh_FAIAD.Sales")

        # Aggregate data to monthly level
        monthly_df = df.withColumn("Month", month("InvoiceDate"))\
                    .withColumn("Year", year("InvoiceDate"))\
                    .groupBy("Year", "Month")\
                    .sum("Quantity")\
                    .orderBy("Year", "Month")

        # Convert to Pandas DataFrame and prepare for Prophet
        pandas_df = monthly_df.toPandas()
        pandas_df['ds'] = pd.to_datetime(pandas_df[['Year', 'Month']].assign(DAY=1))
        pandas_df['y'] = pandas_df['sum(Quantity)']

        # Fit the Prophet model
        model = Prophet(yearly_seasonality=True, weekly_seasonality=False,daily_seasonality=False)
        model.fit(pandas_df[['ds, 'y']])

        # Create a DataFrame for future predictions (e.g., next 12 months)
        future = model.make_future_dataframe(periods=12, freq='M')

        # Forecast
        forecast = model.predict(future)

        # Plotting the forecast
        model.plot(forecast)
        model.plot_components(forecast)
        ``````

39. 解释**代码**的每个步骤（匹配记录作为注释提供）。
40. 通过选择单元格旁边的**播放**按钮执行代码。
 
    引导参与者浏览创建的三个图表（如下）。我们有截至 2023 年 4 月的实际数据，并预测 12 个月的数据。

    请注意，**第一个图表**删除了截至 2024 年 4 月的季节性和预测。
    第二个图表删除了截至 2024 年 4 月的趋势并向预测添加了季节性。
 
    **第三个图表**使用趋势和季节性进行预测。该图表还提供了上限和下限。
 
41. 创建**新单元格。**
42. 将以下**代码**添加到单元格中：

    ```
    display(forecast)
    #将预测数据写入表中
    spark.createDataFrame(forecast).write.saveAsTable("Sales_Forecast", mode="overwrite")
    ```

43. 通过选择**播放**按钮执行单元格。
 
44. 引导参与者浏览**显示的数据。**
45. 向用户显示已创建新表：**sales_forecast**
 
46. **查询**表并向用户显示表的内容。
