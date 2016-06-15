# spring-sqlstatementloader
Loads multiple SQL files with less code and less hassle.

Dependencies:
  Spring
  SLF4J

## Usage

```
  static final Logger LOG = LoggerFactory.getLogger(ServletController.class);
  static final SqlStatementLoader loader;

  static {
    loader = new SqlStatementLoader(Thread.currentThread()
				.getContextClassLoader());
    //Note: the *.sql pattern is automatically appended to whatever pattern you provide.
    loader.loadStatementsByPattern("some/resource/directory");
  }
  @RequestMapping("/")
  public String index(HttpServletRequest request,
			HttpServletResponse response, Model model){
			    jdbcTemplate.query(loader.get("some_sql_statement"));
			}
```
