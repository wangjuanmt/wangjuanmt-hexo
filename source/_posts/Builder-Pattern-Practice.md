---
title: Builder-Pattern-Practice-In-TestRail
date: 2017-11-28 17:33:52
tags: java, Builder Pattern, TestRail
---


```
public class TestRailEntity {
    public String url;
    public TestRailUser testRailUser;
    public int planId;
    public int runId;
    public int suiteId;
    public int projectId;

    public static class Builder {
        // Required parameters
        private String url;
        private TestRailUser testRailUser;

        // Optional parameters
        private int planId;
        private int runId;
        private int suiteId;
        private int projectId;

        public Builder(String url, TestRailUser testRailUser) {
            this.url = url;
            this.testRailUser = testRailUser;
        }

        public Builder PlanId(int val) {
            this.planId = val;
            return this;
        }

        public Builder RunId(int val) {
            this.runId = val;
            return this;
        }

        public Builder SuiteId(int val) {
            this.suiteId = val;
            return this;
        }

        public Builder ProjectId(int val) {
            this.projectId = projectId;
            return this;
        }

        public TestRailEntity build() {
            return new TestRailEntity(this);
        }
    }

    private TestRailEntity(Builder builder) {
        this.url = builder.url;
        this.testRailUser = builder.testRailUser;
        this.planId = builder.planId;
        this.runId = builder.runId;
        this.suiteId = builder.suiteId;
        this.projectId = builder.projectId;
    }
}
```

Now we can call it as 

```
testRailEntity = new TestRailEntity.Builder(TESTRAIL_URL, TESTRAIL_USER_INSTANCE)
                    .PlanId(testRailTestPlanId)
                    .RunId(testRailTestRunId)
                    .SuiteId(testRailTestSuiteId).build();
```