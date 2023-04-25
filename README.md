## Allure Gradle Plugin Cache Failure Reproducer Project

### Build scans
1. First run: https://scans.gradle.com/s/icuh2264l2icy
2. Second run: https://scans.gradle.com/s/tmyymdsn62dmq

### Steps to reproduce:

1. run `./gradlew :app:testDebugUnitTest --scan`
2. delete `/app/build` folder
3. rerun `./gradlew :app:testDebugUnitTest --scan`

#### Expected:
The `:app:testDebugUnitTest` task should pull from local build cache

#### Actual:
The `:app:testDebugUnitTest` task fails to pull from local build cache due to a misconfiguration of the allure 
gradle plugin:

```
The task was not up-to-date because of the following reasons:	
    Output property '$1$1' file app/build/allure-results has been removed.	
    Output property '$1$1' file app/build/allure-results/3d190374-f7ea-49dd-84e4-35154f5d66ff-result.json has been removed.	
    Output property '$1$1' file app/build/allure-results/executor.json has been removed.	

Cache key	e41500b39f37e48c49236439e9a16431	
Not cacheable	Non cacheable tree output: Output property '$1$1' contains a file tree.
```