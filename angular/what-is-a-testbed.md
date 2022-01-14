# What is a TestBed?

When using the CLI, component spec files come with TestBed by default. The purpose of TestBed is to create a testing module - an @NgModule class - complete with DOM and defined dependencies.

```javascript
describe('OverviewComponent', () => {
  let component: OverviewComponent;
  let fixture: ComponentFixture<OverviewComponent>;
  let overviewService: OverviewService;
  let httpClient: HttpClient;
  let store: MockStore;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      imports: [HttpClientTestingModule],
      providers: [HttpClient, provideMockStore({ initialState })],
      declarations: [OverviewComponent]
    }).compileComponents();

    httpClient = TestBed.inject(HttpClient);
    store = TestBed.inject(MockStore);
    overviewService = TestBed.inject(OverviewService);
  });

  beforeEach(() => {
    fixture = TestBed.createComponent(OverviewComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });
});
```

Using the "configureTestingModule" function, TestBed can create a complete module with mocked imports, providers, declarations, and so on. 

This mocked module can then create a fixture of the component, in the example above "OverviewComponent", which can then be tested.