#Tracking Channel

## Structure Diagram
```dot
digraph G
{
  node [shape = record];
  svctrl [label = "{ struct sv_ctrl | ... }"];

  trkchan [label = "{ struct trk_channel | ... }"];
  bitsync [label = "{ struct trk_bitsync | ... }"];

  acqchan [label = "{ struct acq_channel | ... }"];
  acqmode [label = "{ struct acq_searchmode | ... }"];
  acqcfg [label = "{ struct acq_searchcfg | <searchcfg> | ... }"];

  acqchan -> svctrl -> acqchan;
  trkchan -> svctrl -> trkchan;
  svctrl -> acqmode -> acqcfg;
  svctrl -> acqcfg:searchcfg
  trkchan -> bitsync;
}
```

## Declaration
```c
struct trk_channel
{
};


void trkchan_init(unsigned chansize);
struct trk_channel *trkchan_deploy(struct sv_ctrl *svctrl);
void trkchan_kill(struct trk_channel *trkchan);

/**
 * Number of tracking channel occupied.
 */
unsigned trkchan_occupied(void);

void trkchan_gc(void);

struct trkchan_bitsync *trkchan_bitsync_alloc(void);
void trkchan_bitsync_dealloc(struct trkchan_bitsync *bitsync);


```
