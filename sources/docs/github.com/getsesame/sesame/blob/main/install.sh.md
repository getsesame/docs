# Source: https://github.com/getsesame/sesame/blob/main/install.sh

[getsesame](https://github.com/getsesame) / **[sesame](https://github.com/getsesame/sesame)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fsesame) You must be signed in to change notification settings
- [Fork 0](https://github.com/login?return_to=%2Fgetsesame%2Fsesame)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fsesame)
 

 

## FilesExpand file tree

 main

/

# install.sh

Copy path

Blame

More file actions

Blame

More file actions

## Latest commit

## History

[History](https://github.com/getsesame/sesame/commits/main/install.sh)

History

executable file

·

311 lines (255 loc) · 8.11 KB

 main

/

# install.sh

Copy path

Top

## File metadata and controls

- Code
 
- Blame
 

executable file

·

311 lines (255 loc) · 8.11 KB

[Raw](https://github.com/getsesame/sesame/raw/refs/heads/main/install.sh)

Copy raw file

Download raw file

Open symbols panel

Edit and raw actions

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

67

68

69

70

71

72

73

74

75

76

77

78

79

80

81

82

83

84

85

86

87

88

89

90

91

92

93

94

95

96

97

98

99

100

101

102

103

104

105

106

107

108

109

110

111

112

113

114

115

116

117

118

119

120

121

122

123

124

125

126

127

128

129

130

131

132

133

134

135

136

137

138

139

140

141

142

143

144

145

146

147

148

149

150

151

152

153

154

155

156

157

158

159

160

161

162

163

164

165

166

167

168

169

170

171

172

173

174

175

176

177

178

179

180

181

182

183

184

185

186

187

188

189

190

191

192

193

194

195

196

197

198

199

200

201

202

203

204

205

206

207

208

209

210

211

212

213

214

215

216

217

218

219

220

221

222

223

224

225

226

227

228

229

230

231

232

233

234

235

236

237

238

239

240

241

242

243

244

245

246

247

248

249

250

251

252

253

254

255

256

257

258

259

260

261

262

263

264

265

266

267

268

269

270

271

272

273

274

275

276

277

278

279

280

281

282

283

284

285

286

287

288

289

290

291

292

293

294

295

296

297

298

299

300

301

302

303

304

305

306

307

308

309

310

311

#!/bin/sh

# Sesame sesame installer

# Usage: curl -fsSL https://getsesame.dev/install.sh | sh

set -eu

REPO="getsesame/sesame"

BINARY\_NAME="sesame"

DEFAULT\_PREFIX="/usr/local/bin"

# --- Output helpers ---

has\_tty() { \[ \-t 1 \]; }

if has\_tty; then

BOLD='\\033\[1m'

DIM='\\033\[2m'

GREEN='\\033\[0;32m'

RED='\\033\[0;31m'

YELLOW='\\033\[0;33m'

CYAN='\\033\[0;36m'

RESET='\\033\[0m'

else

BOLD='' DIM='' GREEN='' RED='' YELLOW='' CYAN='' RESET=''

fi

info() { printf " %b\\n" "$\*"; }

ok() { printf " %b%b%b\\n" "$GREEN" "$\*" "$RESET"; }

warn() { printf " %b%b%b\\n" "$YELLOW" "$\*" "$RESET"; }

err() { printf " %b%b%b\\n" "$RED" "$\*" "$RESET" \>&2; }

die() { err "$@"; exit 1; }

# --- Argument parsing ---

VERSION=""

PREFIX=""

UNINSTALL=0

HELP=0

while \[ $# \-gt 0 \]; do

case "$1" in

\--version) VERSION="$2"; shift 2 ;;

\--prefix) PREFIX="$2"; shift 2 ;;

\--uninstall) UNINSTALL=1; shift ;;

\--help|-h) HELP=1; shift ;;

\*) die "Unknown option: $1. Run with --help for usage." ;;

esac

done

if \[ "$HELP" \= 1 \]; then

cat <<'USAGE'

Sesame sesame installer

Usage:

curl -fsSL https://getsesame.dev/install.sh | sh

curl -fsSL https://getsesame.dev/install.sh | sh -s -- \[OPTIONS\]

Options:

\--version <ver> Install a specific version (e.g., v0.1.0)

\--prefix <dir> Install location (default: /usr/local/bin)

\--uninstall Remove sesame

\--help Show this message

USAGE

exit 0

fi

# --- Platform detection ---

detect\_platform() {

OS="$(uname -s)"

ARCH="$(uname -m)"

case "$OS" in

Darwin) OS="darwin" ;;

Linux) OS="linux" ;;

\*) die "Unsupported OS: $OS" ;;

esac

case "$ARCH" in

x86\_64|amd64) ARCH="x86\_64" ;;

arm64|aarch64) ARCH="arm64" ;;

\*) die "Unsupported architecture: $ARCH" ;;

esac

PLATFORM="${OS}\-${ARCH}"

}

# --- Version resolution ---

resolve\_version() {

if \[ \-n "$VERSION" \]; then

# Ensure version starts with 'v'

case "$VERSION" in

v\*) ;;

\*) VERSION="v${VERSION}" ;;

esac

return

fi

info "Fetching latest version..."

VERSION=$(curl -fsSL "https://api.github.com/repos/${REPO}/releases/latest" \\

| grep '"tag\_name"' \\

| sed -E 's/.\*"tag\_name": \*"(\[^"\]+)".\*/\\1/')

if \[ \-z "$VERSION" \]; then

die "Could not determine latest version. Specify one with --version."

fi

}

# --- Install location ---

resolve\_prefix() {

if \[ \-n "$PREFIX" \]; then

return

fi

if \[ \-w "$DEFAULT\_PREFIX" \]; then

PREFIX="$DEFAULT\_PREFIX"

elif \[ \-w "$HOME/.local/bin" \] || mkdir -p "$HOME/.local/bin" 2>/dev/null; then

PREFIX="$HOME/.local/bin"

else

PREFIX="$DEFAULT\_PREFIX"

fi

}

ensure\_writable() {

if \[ ! \-w "$PREFIX" \]; then

err "Cannot write to ${PREFIX}"

info ""

info "Run with sudo:"

info " ${CYAN}curl -fsSL https://getsesame.dev/install.sh | sudo sh${RESET}"

info ""

info "Or install to ~/.local/bin:"

info " ${CYAN}curl -fsSL https://getsesame.dev/install.sh | sh -s -- --prefix ~/.local/bin${RESET}"

exit 1

fi

}

# --- PATH check ---

check\_path() {

case ":$PATH:" in

\*":${PREFIX}:"\*) return 0 ;;

esac

SHELL\_NAME="$(basename "${SHELL:-/bin/sh}")"

case "$SHELL\_NAME" in

zsh) PROFILE="$HOME/.zshrc" ;;

bash) PROFILE="$HOME/.bashrc" ;;

\*) PROFILE="$HOME/.profile" ;;

esac

warn "${PREFIX} is not in your PATH."

info ""

info "Add it by running:"

info " ${CYAN}echo 'export PATH=\\"${PREFIX}:\\$PATH\\"' >> ${PROFILE}${RESET}"

info " ${CYAN}source ${PROFILE}${RESET}"

info ""

}

# --- Uninstall ---

do\_uninstall() {

resolve\_prefix

TARGET="${PREFIX}/${BINARY\_NAME}"

LIBDIR="$(dirname "$PREFIX")/lib/sesame"

printf "\\n"

info "${BOLD}sesame${RESET} - secret broker CLI"

info ""

if \[ ! \-e "$TARGET" \] && \[ ! \-L "$TARGET" \] && \[ ! \-d "$LIBDIR" \]; then

warn "sesame is not installed at ${TARGET}"

exit 0

fi

rm -f "$TARGET"

rm -rf "$LIBDIR"

ok "sesame removed from ${TARGET}"

exit 0

}

# --- Download and verify ---

download\_binary() {

ARTIFACT="${BINARY\_NAME}\-${PLATFORM}.tar.gz"

DOWNLOAD\_URL="https://github.com/${REPO}/releases/download/${VERSION}/${ARTIFACT}"

CHECKSUM\_URL="${DOWNLOAD\_URL}.sha256"

TMP\_DIR="$(mktemp -d)"

trap 'rm -rf "$TMP\_DIR"' EXIT

printf " Downloading sesame %b%s%b... " "$BOLD" "$VERSION" "$RESET"

if ! curl -fsSL -o "${TMP\_DIR}/${ARTIFACT}" "$DOWNLOAD\_URL"; then

printf "\\n"

die "Download failed. Check that version ${VERSION} exists at:"

die " https://github.com/${REPO}/releases/tag/${VERSION}"

fi

printf "done\\n"

printf " Verifying checksum... "

if curl -fsSL -o "${TMP\_DIR}/${ARTIFACT}.sha256" "$CHECKSUM\_URL" 2>/dev/null; then

EXPECTED="$(awk '{print $1}' "${TMP\_DIR}/${ARTIFACT}.sha256")"

if command -v sha256sum \>/dev/null 2>&1; then

ACTUAL="$(sha256sum "${TMP\_DIR}/${ARTIFACT}" | awk '{print $1}')"

else

ACTUAL="$(shasum -a 256 "${TMP\_DIR}/${ARTIFACT}" | awk '{print $1}')"

fi

if \[ "$EXPECTED" != "$ACTUAL" \]; then

printf "\\n"

die "Checksum mismatch! Expected ${EXPECTED}, got ${ACTUAL}."

die "The download may be corrupted. Please try again."

fi

printf "ok\\n"

else

warn "skipped (no checksum file found)"

fi

# Unpack the app once, here, into a lib dir next to the bin prefix, then

# symlink the launcher onto PATH. The bundle is already extracted, so

# running \`sesame\` no longer unpacks 37 MB to /tmp on every invocation.

LIBDIR="$(dirname "$PREFIX")/lib/sesame"

tar -xzf "${TMP\_DIR}/${ARTIFACT}" -C "$TMP\_DIR"

rm -rf "$LIBDIR"

mkdir -p "$(dirname "$LIBDIR")"

mv "${TMP\_DIR}/${BINARY\_NAME}" "$LIBDIR"

chmod +x "${LIBDIR}/${BINARY\_NAME}"

ln -sf "${LIBDIR}/${BINARY\_NAME}" "${PREFIX}/${BINARY\_NAME}"

}

# --- Skill install ---

install\_skill() {

# First -y is for npx (auto-accept package install).

# --yes --global --all pass through to the \`skills\` CLI itself: skip every

# confirmation, install to the user-level agent dir, and target every

# detected agent. </dev/null forces the prompt library to give up

# immediately on its TTY check instead of hanging when stdin is the

# curl-piped installer.

SKILL\_CMD="npx -y skills add getsesame/skills --yes --global --all"

SKILL\_MANUAL="npx skills add getsesame/skills"

if ! command -v npx \>/dev/null 2>&1; then

info "${BOLD}Install Sesame skill${RESET} (requires Node.js)"

info " ${CYAN}${SKILL\_MANUAL}${RESET}"

info ""

return

fi

info "${BOLD}Installing Sesame skill...${RESET}"

if $SKILL\_CMD </dev/null; then

ok "Sesame skill installed"

else

warn "Skill install failed. Run manually:"

info " ${CYAN}${SKILL\_MANUAL}${RESET}"

fi

info ""

}

# --- Existing install detection ---

check\_existing() {

TARGET="${PREFIX}/${BINARY\_NAME}"

if \[ \-f "$TARGET" \]; then

CURRENT="$("$TARGET" --version 2>/dev/null || echo "unknown")"

info "Current: ${DIM}${CURRENT}${RESET}"

info "Latest: ${BOLD}${VERSION}${RESET}"

info ""

fi

}

# --- Main ---

main() {

if \[ "$UNINSTALL" \= 1 \]; then

do\_uninstall

fi

detect\_platform

resolve\_version

resolve\_prefix

ensure\_writable

printf "\\n"

info "${BOLD}sesame${RESET} - secret broker CLI"

info ""

info "Platform: ${OS} (${ARCH})"

info "Location: ${PREFIX}/${BINARY\_NAME}"

info ""

check\_existing

download\_binary

info ""

ok "sesame installed successfully!"

info ""

install\_skill

info "Get started:"

info " ${CYAN}sesame login${RESET} Register this device"

info " ${CYAN}sesame status${RESET} Check agent status"

info " ${CYAN}sesame --help${RESET} See all commands"

info ""

info "Docs: ${CYAN}https://getsesame.dev/docs${RESET}"

printf "\\n"

check\_path

}

main